# Godot 4 图片资源提取工具

从 Godot 4 项目的 `.godot/imported` 缓存中提取图片资源文件。

## 功能

- 自动提取 `.ctex` 文件中的图片数据
- 保持原始文件扩展名（.png, .jpg, .svg, .webp 等）
- 支持任何 Godot 4 项目路径
- 批量处理，自动跳过已存在文件

## 使用方法

### 基本用法

```bash
# 使用当前目录（当前目录必须是 Godot 项目）
python extract_godot_images.py

# 指定项目路径
python extract_godot_images.py C:\MyGame

# 路径包含空格时使用引号
python extract_godot_images.py "D:\Godot Projects\MyGame"
```

### 指定输出目录

```bash
python extract_godot_images.py C:\MyGame -o D:\Output
```

## 工作原理

1. 扫描项目目录下的 `.godot/imported/` 文件夹
2. 查找所有 `.ctex` 纹理缓存文件
3. 从缓存中提取 WebP 格式的图片数据
4. 根据原始文件名恢复文件扩展名
5. 保存到输出目录

## 提取示例

| 缓存文件名 | 提取后文件名 |
|-----------|-------------|
| `icon.svg-218a8f2b.ctex` | `icon.svg` |
| `player.png-a1b2c3d.ctex` | `player.png` |
| `bg.jpg-xyz789.ctex` | `bg.jpg` |

## 注意事项

- 确保项目已经用 Godot 4 编辑器打开过（生成导入缓存）
- 提取的文件保存在 `项目目录/extracted_images/` 或指定的输出目录
- 如果目标文件已存在，会自动跳过

## 系统要求

- Python 3.6+
- Godot 4.x 项目（已生成导入缓存）

## 许可证

MIT License
