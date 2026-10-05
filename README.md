# RK_00006
# Luminosity_reading.py

def has_exoplanet(readings):
    values = []
    for char in readings:
        if '0' <= char <= '9':
            values.append(int(char))
        elif 'A' <= char <= 'Z':
            values.append(ord(char) - ord('A') + 10)
            
    if not values:
        return False
        
    avg_luminosity = sum(values) / len(values)
    threshold = 0.8 * avg_luminosity
    
    return any(val <= threshold for val in values)

if __name__ == "__main__":
    tests = [
        ("665544554", False),
        ("FGFFCFFGG", True),
        ("MONOPLONOMONPLNOMPNOMP", False),
        ("FREECODECAMP", True),
        ("9AB98AB9BC98A", False),
        ("ZXXWYZXYWYXZEGZXWYZXYGEE", True)
    ]

    
    for i, (inp, expected) in enumerate(tests, 1):
        result = has_exoplanet(inp)
        print(f"Test {i}: {inp} -> {result} (Expected: {expected})")
