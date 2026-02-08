#code


import numpy as np
import librosa
import os

def encode_audio_to_bytebeat(file_path):
    # Setup Parameters
    target_sr = 96000
    base_name = os.path.basename(file_path)
    output_file = "bad_apple_96khz_encoded.txt"
    
    print(f"--- 🌌 Initializing 96kHz Super Hi-Res Encoding: {base_name} ---")
    
    # 1. Load and Resample
    print(f"[*] Resampling audio to {target_sr}Hz...")
    data, _ = librosa.load(file_path, sr=target_sr)
    
    # 2. Normalize and Convert to 16-bit
    print("[*] Normalizing amplitudes (16-bit Depth)...")
    data = (data.astype(np.float32) / (np.max(np.abs(data)) + 1e-6)) * 0.9
    uint16_data = ((data + 1) / 2 * 65535).astype(np.uint32)
    
    # 3. Hex Conversion
    print("[*] Converting PCM to Hex Stream (This may take a moment)...")
    hex_data = "".join([format(x, '04x') for x in uint16_data])

    # 4. Write Output with Line Chunking (Crucial for Browser/GitHub Stability)
    print(f"[*] Exporting to {output_file}...")
    with open(output_file, "w", encoding="utf-8") as f:
        f.write('// 🌐 ULTIMATE HI-RES BYTBEBEAT | 96,000Hz | 16-bit\n')
        f.write('// Instructions: Set Sample Rate to 96000 and Mode to Floatbeat\n\n')
        
        f.write('h = ""\n')
        
        # Chunking: Write in segments of 5,000 chars to avoid memory overflow
        chunk_size = 5000
        for i in range(0, len(hex_data), chunk_size):
            f.write(f'h += "{hex_data[i:i+chunk_size]}",\n')
        
        f.write('\n// Playback Logic\n')
        f.write('p = t * 4,\n')
        f.write('v = parseInt(h.slice(p, p + 4), 16),\n')
        f.write('s = (v / 32767.5) - 1,\n')
        f.write('isNaN(s) ? 0 : [s, s]')

    print("\n" + "="*60)
    print(f"💎 SUCCESS: High-Resolution Data Generated")
    print(f"📁 Path: {os.path.abspath(output_file)}")
    print(f"📏 Total Characters: {len(hex_data):,}")
    print("="*60)

# Path to your file
file_path = r""#here
encode_audio_to_bytebeat(file_path)
