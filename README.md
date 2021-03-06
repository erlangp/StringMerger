# StringMerger

### Installation

Just copy `StringMerger.java` file to your project

### How to use

Example:

```java
// define layers
ArrayList<StringMerger.Layer> layers = new ArrayList<>();
layers.add(new StringMerger.Layer("left", 4, "Abcdefghijklmnopqrstuvwxyz"));
layers.add(new StringMerger.Layer("left", 0, "6789"));
layers.add(new StringMerger.Layer("right", 0, "@Rp20.000"));
layers.add(new StringMerger.Layer("right", 9, "HELLO"));

StringMerger merger = new StringMerger(30, ' ', layers);

// config
//merger.setMaxLength(30);
//merger.setBgChar(' ');
//merger.setLayers(layers);

String result = merger.getMergedString();

System.out.println(result); // output: "6789AbcdefghijklHELLO@Rp20.000"
```

### How it works

Concept:

```
Bg Char: "                              " ---> initial 30
Layer 1: "    Abcdefghijklmnopqrstuvwxyz" ---> left  4
Layer 2: "6789                          " ---> left  0
Layer 3: "                     @Rp20.000" ---> right 0 ---> "rstuvwxyz" will be replaced
Layer 4: "                HELLO         " ---> right 9 ---> "mnopq" will be replaced

Result : "6789AbcdefghijklHELLO@Rp20.000"
```
