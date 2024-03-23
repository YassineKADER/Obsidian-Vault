# Adapter

`L'Adaptateur est un patron de conception` `structurel` qui permet à des objets avec des interfaces incompatibles de collaborer.

![[Untitled 43.png|Untitled 43.png]]

Imaginez un système existant utilisant une classe avec une interface obsolète, et vous devez intégrer un nouveau composant avec une interface moderne. Utilisez le patron Adaptateur pour permettre au nouveau composant de collaborer de manière transparente avec le système existant sans modifier son code, assurant ainsi la compatibilité entre les deux interfaces.

Example:

![[Untitled 1 22.png|Untitled 1 22.png]]

```Java
public class RoundHole {
    private double radius;

    public RoundHole(double radius) {
        this.radius = radius;
    }

    public double getRadius() {
        return radius;
    }

    public boolean fits(RoundPeg peg) {
        boolean result;
        result = (this.getRadius() >= peg.getRadius());
        return result;
    }
}

public class RoundPeg {
    private double radius;

    public RoundPeg() {}

    public RoundPeg(double radius) {
        this.radius = radius;
    }

    public double getRadius() {
        return radius;
    }
}

public class SquarePeg {
    private double width;

    public SquarePeg(double width) {
        this.width = width;
    }

    public double getWidth() {
        return width;
    }

    public double getSquare() {
        double result;
        result = Math.pow(this.width, 2);
        return result;
    }
}

public class SquarePegAdapter extends RoundPeg {
    private SquarePeg peg;

    public SquarePegAdapter(SquarePeg peg) {
        this.peg = peg;
    }

    @Override
    public double getRadius() {
        double result;
        // Calculate a minimum circle radius, which can fit this peg.
        result = (Math.sqrt(Math.pow((peg.getWidth() / 2), 2) * 2));
        return result;
    }
}

public class Demo {
    public static void main(String[] args) {
        // Round fits round, no surprise.
        RoundHole hole = new RoundHole(5);
        RoundPeg rpeg = new RoundPeg(5);
        if (hole.fits(rpeg)) {
            System.out.println("Round peg r5 fits round hole r5.");
        }

        SquarePeg smallSqPeg = new SquarePeg(2);
        SquarePeg largeSqPeg = new SquarePeg(20);
        // hole.fits(smallSqPeg); // Won't compile.

        // Adapter solves the problem.
        SquarePegAdapter smallSqPegAdapter = new SquarePegAdapter(smallSqPeg);
        SquarePegAdapter largeSqPegAdapter = new SquarePegAdapter(largeSqPeg);
        if (hole.fits(smallSqPegAdapter)) {
            System.out.println("Square peg w2 fits round hole r5.");
        }
        if (!hole.fits(largeSqPegAdapter)) {
            System.out.println("Square peg w20 does not fit into round hole r5.");
        }
    }
}
```

# Composite

Le `Composite` est un patron de `conception structurel` qui permet de `composer des objets` en `structures arborescentes`, puis de travailler avec `ces structures comme s'il s'agissait d'objets individuels`.

![[Untitled 2 20.png|Untitled 2 20.png]]

Imaginez un système graphique avec des formes telles que des cercles et des rectangles. Utilisez le patron Composite pour traiter uniformément des formes individuelles et des groupes de formes, permettant le dessin de scènes complexes en combinant les formes dans une structure arborescente. Les clients peuvent ainsi interagir avec l'ensemble de la scène ou des formes individuelles de manière transparente.

Example:

![[Untitled 3 20.png|Untitled 3 20.png]]

```Java
import java.util.ArrayList;
import java.util.List;

// Component: Graphic interface
interface Graphic {
    void draw();
}

// Leaf: Dot class
class Dot implements Graphic {
    @Override
    public void draw() {
        System.out.println("Drawing a Dot");
    }
}

// Leaf: Circle class extending Dot
class Circle extends Dot {
    @Override
    public void draw() {
        System.out.println("Drawing a Circle");
    }
}

// Composite: CompoundGraphic class
class CompoundGraphic implements Graphic {
    private List<Graphic> graphics = new ArrayList<>();

    public void add(Graphic graphic) {
        graphics.add(graphic);
    }

    @Override
    public void draw() {
        System.out.println("Drawing a Compound Graphic");
        for (Graphic graphic : graphics) {
            graphic.draw();
        }
    }
}

// Client: ImageEditor class
class ImageEditor {
    private Graphic graphic;

    public ImageEditor(Graphic graphic) {
        this.graphic = graphic;
    }

    public void drawImage() {
        graphic.draw();
    }
}

// Main class for testing
public class Main {
    public static void main(String[] args) {
        // Create leaf objects
        Dot dot = new Dot();
        Circle circle = new Circle();

        // Create composite object
        CompoundGraphic compoundGraphic = new CompoundGraphic();
        compoundGraphic.add(dot);
        compoundGraphic.add(circle);

        // Use the composite in the image editor
        ImageEditor imageEditor = new ImageEditor(compoundGraphic);
        imageEditor.drawImage();
    }
}
```

# Decorator

Le `Decorator` est un patron de conception `structurel` qui vous permet `d'ajouter de nouvelles fonctionnalités` à des `objets en les enveloppant` dans `des objets spéciaux contenant ces fonctionnalités supplémentaires`.

![[Untitled 4 19.png|Untitled 4 19.png]]

Imaginez une interface de base `DataSource` pour la lecture de données. Utilisez le patron Decorator pour étendre sa fonctionnalité en créant un `DataSourceDecorator` qui ajoute le chiffrement aux données. Ainsi, vous pouvez envelopper n'importe quelle source de données existante avec la capacité de chiffrement sans modifier son code d'origine.

![[example 2.png|example 2.png]]

```Java
// DataSource interface
interface DataSource {
    String readData();
}

// Concrete implementation of DataSource
class FileDataSource implements DataSource {
    private String data;

    public FileDataSource(String data) {
        this.data = data;
    }

    @Override
    public String readData() {
        return "Reading data from file: " + data;
    }
}

// Decorator class
abstract class DataSourceDecorator implements DataSource {
    private final DataSource dataSource;

    public DataSourceDecorator(DataSource dataSource) {
        this.dataSource = dataSource;
    }

    @Override
    public String readData() {
        return dataSource.readData();
    }
}

// Concrete decorator adding encryption
class EncryptionDecorator extends DataSourceDecorator {
    public EncryptionDecorator(DataSource dataSource) {
        super(dataSource);
    }

    @Override
    public String readData() {
        String originalData = super.readData();
        return "Encrypting data: " + originalData;
    }
}

// Client code
public class Main {
    public static void main(String[] args) {
        // Original data source
        DataSource fileDataSource = new FileDataSource("Sample data");

        // Decorating with encryption
        DataSource encryptedDataSource = new EncryptionDecorator(fileDataSource);

        // Reading data through the decorated source
        String result = encryptedDataSource.readData();
        System.out.println(result);
    }
}
```

# Facade

La `Facade` est un patron de `conception structurel` qui `fournit une interface simplifiée` à une bibliothèque, un framework ou tout autre ensemble complexe de classes.

![[Untitled 5 17.png|Untitled 5 17.png]]

Supposons que vous ayez un système complexe de conversion vidéo avec plusieurs classes et fonctionnalités, et que vous souhaitiez simplifier le processus pour les clients. Vous pouvez utiliser le patron de conception Facade pour créer une classe `**VideoConverterFacade**` qui offre une interface simple pour les tâches courantes de conversion vidéo.

![[Untitled 6 16.png|Untitled 6 16.png]]

Example:

```Java
// Classes complexes du sous-système
class VideoCodec {
    public String compresser(String fichierVideo) {
        System.out.println("Compression de la vidéo : " + fichierVideo);
        // Détails de l'implémentation
        return "Compressé_" + fichierVideo;
    }
}

class AudioCodec {
    public String convertir(String fichierVideo) {
        System.out.println("Conversion audio de la vidéo : " + fichierVideo);
        // Détails de l'implémentation
        return "AudioConverti_" + fichierVideo;
    }
}

class ConvertisseurFormat {
    public String convertir(String fichierVideo, String formatCible) {
        System.out.println("Conversion du format vidéo : " + fichierVideo);
        // Détails de l'implémentation
        return "FormatConverti_" + formatCible + "_" + fichierVideo;
    }
}

// Classe Facade
class VideoConverterFacade {
    private VideoCodec videoCodec;
    private AudioCodec audioCodec;
    private ConvertisseurFormat convertisseurFormat;

    public VideoConverterFacade() {
        this.videoCodec = new VideoCodec();
        this.audioCodec = new AudioCodec();
        this.convertisseurFormat = new ConvertisseurFormat();
    }

    public String convertirVideo(String fichierVideo, String formatCible) {
        String videoCompressée = videoCodec.compresser(fichierVideo);
        String audioConverti = audioCodec.convertir(videoCompressée);
        return convertisseurFormat.convertir(audioConverti, formatCible);
    }
}

// Code client
public class Main {
    public static void main(String[] args) {
        VideoConverterFacade videoConverter = new VideoConverterFacade();

        // Conversion simplifiée de la vidéo en utilisant la façade
        String résultat = videoConverter.convertirVideo("videoInput.mp4", "AVI");

        System.out.println("Résultat : " + résultat);
    }
}
```