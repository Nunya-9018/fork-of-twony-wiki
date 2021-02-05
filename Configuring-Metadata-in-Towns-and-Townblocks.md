The Towny API has a list of properties already hooked to towny objects that are editable by Towny plugin developers. While a lot of these are useful in the context of Towny, as an independent plugin developer, you may want to store other custom data within some towny objects. This is the purpose of metadata.

### Why use Metadata as opposed to storing data within your plugin?
* Data not stored in the Towny plugin is decentralized which makes it hard for other devs to see and manipulate your stored data, this is especially problematic if another plugin depends on data from the plugin you are developing. Towny metadata is centralized thus allowing for easy access via documentation, and key-names.
* If your plugin requires external data on different towny objects developing a backend to deal with it, can be cumbersome and time intensive.
* Metadata allows for custom fields in towny objects like the ones already included, ie: pvp, explosions, residents.
* Plugins do not have to worry about towny objects like towns, nations, or residents changing names and losing data associated with them.

### Example plugins using Metadata
Check out [Plugins using Metadata](https://github.com/TownyAdvanced/Towny/wiki/Plugins-using-the-Towny-API#plugins-using-metadata)

### How to use the Metadata within the TownyAPI
The API uses a data field system for storing metadata, which essentially works a key-value storage. Plugins will create their own unique keys, and store a persistent primitive value.

#### Anatomy of Data Fields
- `CustomDataField`
  - `IntegerDataField`
  - `StringDataField`
  - `BooleanDataField`
  - `DecimalDataField`
  - `LongDataField`

Each of the data field hold a specific type of data that can be properly deserialized when towny loads.

### Parts of a `DataField`
Each data field will essentially have three member variables: key, value, and label.
* Key: A unique non-empty string that identifies metadata property. Metadata is not shared between towny objects, so keys only need to be unique against other metadata keys for that specific towny object. However, a good general key should prefix the plugin name before the keyname e.g. `towny_explosion`.
* Value: The value stored in the metadata. This depends on the specific data field chosen. 
* Label: An optional string used to display the metadata on the towny object. For example, a metadata field with the label `Kills` associated with a specific town will show up when the town status of that town is shown (via `/t` or `/t [townname]`. Do not set labels if you want hidden metadata.

## Prerequisites 
1) Make sure that your plugin depends on Towny, you can do this by adding this to your plugin.yml:
     ```yaml
     depends: [Towny]
     ```
2) Add Towny as a dependency to Maven [as described here.](https://github.com/TownyAdvanced/Towny/wiki/TownyAPI#getting-started-with-towny-and-your-ide)

### Registering global metadata with your plugin.
If a plugin registers global metadata, it provides a way for server administrators to add that metadata via in-game commands. This step is not necessary, if a plugin plans on having full control the metadata and does not want admin interaction with the metadata.

The metadata will be registered on load.

```java
public class Plugin extends JavaPlugin {

    private static String keyname = "plugin_intfield"; // This key must be unique to your plugin.
    private static int defaultVal = 0; // This is the default value your data field will have whenever its added to an object.
    private static String label = "Super Duper Int Field"; // Label that will be displayed when the towny object's status is shown.
    private static IntegerDataField myCustomIntegerField = new IntegerDataField(keyname, defaultVal, label);

    // Called when the plugin first loads.
    @Override
    public void onLoad() {
        // Try to register the data field.
        try {
            TownyAPI.getInstance().registerCustomDataField(myCustomIntegerField);
        } catch (KeyAlreadyRegisteredException e) {
            getLogger().warning(e.getMessage()); // A flag with the same key name already exists try again
        }

        getLogger().info("Flag successfully registered!");
    }
    
    public static IntegerDataField getMyCustomIntegerField() {
        return myCustomIntegerField;
    }
}
```
     
### Attaching metadata to towny objects
```java
IntegerDataField idf = new IntegerDataField("plugin_intfield", 10);

// For townblock objects
townblock.addMetaData(idf);

// For town objects
town.addMetaData(idf);

// For nation objects
nation.addMetaData(idf);

// Same for the rest of the towny objects
```

Alternatively, if you want your metadata available to all towns by default you could loop through all of the objects on initialization and add the custom data.


#### Retrieving and modifying custom data fields
```java
private IntegerDataField idf = new IntegerDataField("plugin_idf", 10);

public void manipulateData(TownBlock townBlock) {
    // Check if the townblock has metadata matching they key.
    if (townBlock.hasMeta(idf.getKey())) {
        // Get the generic data field from the townblock.
        CustomDataField cdf = townBlock.getMeta(idf.getKey());
        // Make sure that the datafield is an integer data field which is what 'idf' is.
        if (cdf instanceof IntegerDataField) {
            // Cast the data field to an integer data field.
            IntegerDataField myfield = (IntegerDataField) cdf;
            // Set the value
            myfield.setValue(10);
        }
    } 
}
```

With that you should be able to edit, add and change metadata.

### Full Example Demonstrating CRUD Operations
This example file will demonstrate how to create, read, update, and delete metadata.

```java
public class Plugin extends JavaPlugin {

    private static String keyName = "plugin_key"; // A key name unique to your plugin.
    private static int defaultVal = 0; // Default value of your data field.
    private static String label = "Super Cool Int Field"; // Label for the metadata that will be displayed when status is called for that towny object.
    private static IntegerDataField myCustomIntField = new IntegerDataField(keyName, defaultVal, label);
    
    // Register the metadata globally for admins to add the metadata to objects via in-game commands. 
    @Override
    public void onLoad() {
        // Try to register the data field.
        try {
            TownyAPI.getInstance().registerCustomDataField(myCustomIntField);
        } catch (KeyAlreadyRegisteredException e) {
            getLogger().warning(e.getMessage()); // A flag with the same key name already exists try again
        }

        getLogger().info("Flag successfully registered!");
    }

    // Add metadata (Create)
    public void addMetadataToTown(Town t) {
        // Simply clone the metadata and add it to the town.
        // If the object is not cloned, then every time you change the value for the field,
        // it will change the value across all towny objects that have the metadata.
        
        t.addMetaData(myCustomIntField.clone());
    }

    // Fetch metadata (Read)
    public int getMetaDataFromTown(Town t) {
        // Check that the town has the metadata key.
        if (t.hasMeta(myCustomIntField.getKey())) {
            // Get the metadata from the town using the key.
            CustomDataField cdf = t.getMetaData(myCustomIntField.getKey());
            // Check that it's an IntegerDataField
            if (cdf instanceof IntegerDataField) {
                // Cast to IntegerDataField
                IntegerDataField idf = (IntegerDataField) cdf;

                // Return the read value which is an integer.
                return idf.getValue();
            }
        }

        // Return a default value
        return -1;
    }

    // Update metadata (Update)
    public void updateMetaDataFromTown(Town t, int updatedVal) {
        // Check that the town has the metadata key.
        if (t.hasMeta(myCustomIntField.getKey())) {
            // Get the metadata from the town using the key.
            CustomDataField cdf = t.getMetaData(myCustomIntField.getKey());
            // Check that it's an IntegerDataField
            if (cdf instanceof IntegerDataField) {
                // Cast to IntegerDataField
                IntegerDataField idf = (IntegerDataField) cdf;

                // Update the value
                idf.setValue(updatedVal);
            }
        }
    }

    // Remove metadata (Delete)
    public void removeMetaDataFromTown(Town t) {
        t.removeMetaData(myCustomIntField);
    }
}
```


