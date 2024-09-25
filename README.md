# Houdini Material Path Tool

## Overview
The Houdini Material Path Tool transfers geometry or group names into material paths to ensure consistent material naming.
This tool offers preset options for Unreal, Unity, and custom paths.

## Features
- Dynamically renames material paths based on geometry string or group names.
- Multiple presets (Unreal, Unity).
- Custom naming options available.

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
