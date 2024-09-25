# Material Path Manager

**Material Path Manager** is a powerful and free Houdini tool designed to streamline the process of managing and generate materials in your projects.
This tool automatically generates material names from geometry string attributes, ensuring consistent naming conventions across different platforms such as Mantra, MaterialX, Arnold, etc. and different game engines such as Unity, Unreal.

## Key Features

- **Automatic Material Name Generation**: Generates material names based on geometry string attributes, eliminating the need for manual naming.
- **Custom Material Paths**: Supports user-defined material paths for greater flexibility in material organization.
- **Shader Type Customization**: Allows users to create shader nodes for different renderers (Mantra, MaterialX, Arnold, etc.) based on user input.
- **Path Cleanup**: Removes long paths from geometry names, simplifying material names and improving clarity.
- **Empty Name Exclusion**: Ignores empty or invalid material names to enhance efficiency during material creation.
- **Free and Open Source**: Committed to the philosophy that information should be freely accessible to all.

## Installation

1. Download the repository or clone it using Git:
    ```bash
    git clone https://github.com/zosimpavel/HoudiniTools.git
    ```
2. Place the Houdini asset file (`.hdanc`) into your Houdini project or the `otls` folder.

## Usage

1. Upload geometry using either the file node or FBX Archive.
2. Connect the geometry to the **Material Path Manager** tool.
3. Specify the attribute to parse, typically the “path” or “name” attribute.
4. Generate materials and customize shader types as needed.

## Contribution

Feel free to contribute to the development of **Material Path Manager**. Whether it's reporting bugs, suggesting new features, or contributing code, your input is valuable!

## License

This tool is released under the [MIT License](LICENSE)

## Acknowledgements

Thank you for supporting this project! Together, we can make Houdini a more efficient and powerful tool for artists and technical directors.

## Installation
1. Download the repository or clone it using Git:
    ```bash
    git clone https://github.com/zosimpavel/HoudiniTools.git
    ```
2. Place the Houdini asset file (`.hdanc`) into your Houdini project or the `otls` folder.

## Usage
1. Open Houdini.
2. Import the tool into your scene.
3. Select the preset (Unreal, Unity, Custom) and provide the path to materials.
4. The tool will automatically update material paths based on the geometry name attribute.

## Example
```vex
// Example VEX code used in the tool

// Get the value of the attribute name
string attr_name  = chs('attribute_name');
string name_value = attrib(0, "prim", attr_name, @primnum);

string path_to_materials = detail(0, "path_to_materials");
string material_prefix = detail(0, "material_prefix");
string material_extension = detail(0, "material_extension");

// Create a new attribute shop_materialpath
string shop_materialpath_value = sprintf(path_to_materials + material_prefix + "%s" + material_extension, name_value);

// Set the value for the attribute shop_materialpath
s@shop_materialpath = shop_materialpath_value;
