Contre-exemple sans le Design Pattern Strategy :

Supposons que, au lieu d'utiliser le Design Pattern Strategy, vous décidiez d'implémenter les différentes façons de se déplacer directement dans la classe du personnage.

java  
Copy code  
  

```Java
// Sans utiliser le Design Pattern Strategy

class CharacterWithoutStrategy {
private boolean isFlying;
private boolean isSwimming;
public void fly() {
    isFlying = true;
    isSwimming = false;
    System.out.println("Je vole.");
}

public void swim() {
    isFlying = false;
    isSwimming = true;
    System.out.println("Je nage.");
}

public void walk() {
    isFlying = false;
    isSwimming = false;
    System.out.println("Je marche.");
}

public void performMove() {
    if (isFlying) {
        System.out.println("Je vole.");
    } else if (isSwimming) {
        System.out.println("Je nage.");
    } else {
        System.out.println("Je marche.");
    }
}
```

}  
Problématique sans le Design Pattern Strategy :  

Rigidité du code : Si vous ajoutez une nouvelle façon de se déplacer, comme courir, vous devrez modifier directement la classe CharacterWithoutStrategy. Cela peut entraîner des changements délicats dans le code existant et peut causer des erreurs.  
java  
Copy code  
// Ajout d'une nouvelle façon de se déplacer  
public void run() {  
isFlying = false;  
isSwimming = false;  
System.out.println("Je cours.");  
}  

// Utilisation de la nouvelle façon  
characterWithoutStrategy.run();  
characterWithoutStrategy.performMove(); // Cela nécessite des modifications directes dans la classe  
Difficulté d'extension : Si vous introduisez de nouveaux personnages avec des façons de se déplacer différentes, vous devrez répéter la logique de déplacement pour chaque personnage.  
Comparaison avec le Design Pattern Strategy :  

Avec le Design Pattern Strategy, vous ajoutez simplement une nouvelle implémentation de l'interface MoveStrategy pour chaque nouvelle façon de se déplacer, et vous pouvez changer dynamiquement la stratégie du personnage. Cela évite la modification directe de la classe Character et rend le système plus flexible

```Java
// 1. Créer une interface pour les façons de se déplacer
interface MoveStrategy {
    void move();
}

// 2. Implémenter ces façons de se déplacer
class WalkStrategy implements MoveStrategy {
    @Override
    public void move() {
        System.out.println("Je marche.");
    }
}

class RunStrategy implements MoveStrategy {
    @Override
    public void move() {
        System.out.println("Je cours.");
    }
}

class FlyStrategy implements MoveStrategy {
    @Override
    public void move() {
        System.out.println("Je vole.");
    }
}

// 3. Utiliser ces façons dans un personnage
class Character {
    private MoveStrategy moveStrategy;

    public Character(MoveStrategy moveStrategy) {
        this.moveStrategy = moveStrategy;
    }

    public void setMoveStrategy(MoveStrategy moveStrategy) {
        this.moveStrategy = moveStrategy;
    }

    public void performMove() {
        moveStrategy.move();
    }
}

// 4. Utiliser le personnage avec différentes façons de se déplacer
public class StrategyExample {
    public static void main(String[] args) {
        Character character = new Character(new WalkStrategy());
        character.performMove();  // Affiche : Je marche.

        character.setMoveStrategy(new FlyStrategy());
        character.performMove();  // Affiche : Je vole.
    }
}
```

  

  

2eme example:

```Java
//without using strategy approach

class DataProcessorWithoutStrategy {
    public void processFile(String filePath) {
        if (filePath.endsWith(".csv")) {
            // Process CSV file
            System.out.println("Processing CSV file: " + filePath);
            // Additional CSV processing logic...
        } else if (filePath.endsWith(".json")) {
            // Process JSON file
            System.out.println("Processing JSON file: " + filePath);
            // Additional JSON processing logic...
        } else {
            System.out.println("Unsupported file type: " + filePath);
        }
    }
}
```

```Java
//solution
// Strategy interface
interface FileProcessorStrategy {
    void process(String filePath);
}

// Concrete strategy for CSV files
class CsvFileProcessor implements FileProcessorStrategy {
    @Override
    public void process(String filePath) {
        System.out.println("Processing CSV file: " + filePath);
        // Additional CSV processing logic...
    }
}

// Concrete strategy for JSON files
class JsonFileProcessor implements FileProcessorStrategy {
    @Override
    public void process(String filePath) {
        System.out.println("Processing JSON file: " + filePath);
        // Additional JSON processing logic...
    }
}

// Context class with a dynamic strategy
class DataProcessorWithDynamicStrategy {
    private FileProcessorStrategy fileProcessor;

    public void setFileProcessor(FileProcessorStrategy fileProcessor) {
        this.fileProcessor = fileProcessor;
    }

    public void processFile(String filePath) {
        if (fileProcessor != null) {
            fileProcessor.process(filePath);
        } else {
            System.out.println("No file processor set.");
        }
    }
}

// Client code
public class DynamicStrategyExample {
    public static void main(String[] args) {
        DataProcessorWithDynamicStrategy processor = new DataProcessorWithDynamicStrategy();

        // Initially set the strategy to process CSV files
        processor.setFileProcessor(new CsvFileProcessor());
        processor.processFile("data.csv");

        // Change the strategy at runtime to process JSON files
        processor.setFileProcessor(new JsonFileProcessor());
        processor.processFile("data.json");
    }
}
```