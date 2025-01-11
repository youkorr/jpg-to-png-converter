# JPG to PNG Converter Blueprint for Home Assistant

This Home Assistant blueprint automates the conversion of JPG images to PNG with customizable resolution and compression options. It can process images automatically from a source folder to a destination folder.

## 🌟 Features

- Automatic JPG to PNG conversion
- Source and destination folder management
- Predefined and custom resolution options
- Configurable compression level
- Automatic folder creation (optional)
- Success/error notifications
- Detailed operation logging

## 📋 Prerequisites

- Home Assistant version 2023.3.0 or higher
- Access to Python Script and Shell Command integrations
- File system write permissions

## 🚀 Installation

1. **Enable Required Integrations**
   
   Add these lines to your `configuration.yaml`:
   ```yaml
   python_script:

   shell_command:
     convert: "{{ command }}"

   input_button:
     trigger_conversion:
       name: "Convert JPG to PNG"
   ```

2. **Install the Blueprint**
   - Open Home Assistant
   - Go to "Configuration" → "Automations & Scenes"
   - Click the 3 dots in the top right
   - Select "Blueprints"
   - Click "Import Blueprint"
   - Paste the blueprint URL: `https://github.com/youkorr/jpg-to-png-converter/blob/main/blueprints/jpg_to_png_converter.yaml`

3. **Restart**
   - Restart Home Assistant to apply changes

## ⚙️ Configuration

### Available Options

| Option | Description | Default Value |
|--------|-------------|---------------|
| Input Directory | Path to JPG images | `/config/www/jpg_input` |
| Output Directory | Path for converted PNGs | `/config/www/png_output` |
| Resolution | Preset or custom | `original` |
| Compression | Level (0-9) | `6` |

### Preset Resolutions
- Original (maintains size)
- 1920x1080 (Full HD)
- 1280x720 (HD)
- 800x600
- 320x240
- Custom (format: WxH)

### Compression Levels
- 0: No compression
- 1-3: Light compression
- 4-6: Medium compression (recommended)
- 7-9: Maximum compression

## 🎯 Usage

1. **Create Automation**
   - Go to "Configuration" → "Automations & Scenes"
   - Click "Create Automation"
   - Choose "Create automation from a blueprint"
   - Select "JPG to PNG Converter with Path Management"

2. **Configure Options**
   - Set source and destination paths
   - Choose desired resolution
   - Set compression level
   - Enable/disable automatic folder creation

3. **Triggering**
   - Use the "Convert JPG to PNG" button in the interface
   - Process runs automatically
   - Notification confirms conversion completion

## 📁 Folder Structure

```
config/
├── www/
│   ├── jpg_input/    # Default JPG folder
│   └── png_output/   # Default PNG folder
└── scripts/
    └── convert_jpg_to_png.py   # Auto-generated script
```

## 🔍 Troubleshooting

1. **"No such file or directory" Error**
   - Verify configured paths exist
   - Enable "Create directories if missing" option

2. **Permission Error**
   - Check folder access rights
   - Folders must be readable/writable

3. **Conversion Fails**
   - Check log at `/config/jpg_to_png_converter.log`
   - Ensure source images are valid

## 📝 Logging

Logs are available in:
- `/config/jpg_to_png_converter.log` for converter
- Home Assistant logs for automations

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Report bugs
- Suggest improvements
- Submit pull requests

## 📄 License

This project is licensed under the MIT License. See LICENSE file for details.

## 📧 Support

For questions or issues:
1. Check troubleshooting section first
2. Review logs
3. Open GitHub issue if problem persists

## 🔧 Technical Details

### Script Configuration
The converter script supports several command-line arguments:
```bash
python3 convert_jpg_to_png.py [input_dir] [output_dir] [resolution_preset] [custom_resolution] [compression] [create_dirs]
```

### Resolution Format
Custom resolutions should be specified in WxH format:
```
1920x1080
1280x720
800x600
```

### Error Handling
The script includes comprehensive error handling for:
- Invalid input files
- Permission issues
- Memory constraints
- Invalid resolution formats

### Performance
- Optimized for batch processing
- Memory-efficient image handling
- Progress logging for large batches

## 📊 Examples

### Basic Configuration
```yaml
input_directory: "/config/www/cameras"
output_directory: "/config/www/processed"
resolution_preset: "1280x720"
compression_level: 6
```

### Custom Resolution
```yaml
input_directory: "/config/www/snapshots"
output_directory: "/config/www/converted"
resolution_preset: "custom"
custom_resolution: "1600x900"
compression_level: 8
```

## 🔄 Update History

### Version 1.1.0
- Added batch processing
- Improved error handling
- Added custom resolution support
- Enhanced logging

### Version 1.0.0
- Initial release
- Basic conversion functionality
- Preset resolutions
- Compression support

