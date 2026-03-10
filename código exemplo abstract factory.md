
**Data:** 2025-11-06
**keyboards:** 
**links internos:** 
___

```

// --- PASSO 2: Declare interfaces de produto abstratas ---
// Temos dois tipos de produtos: Botão e Caixa de Seleção.

interface Button {
    void paint();
}

interface Checkbox {
    void paint();
}

// --- PASSO 2 (continuação): Implemente as classes concretas do produto ---
// Agora, criamos as variantes (família Windows).

class WindowsButton implements Button {
    @Override
    public void paint() {
        System.out.println("Renderizando um botão no estilo Windows.");
    }
}

class WindowsCheckbox implements Checkbox {
    @Override
    public void paint() {
        System.out.println("Renderizando uma caixa de seleção no estilo Windows.");
    }
}

// E as outras variantes (família macOS).
class MacOSButton implements Button {
    @Override
    public void paint() {
        System.out.println("Renderizando um botão no estilo macOS.");
    }
}

class MacOSCheckbox implements Checkbox {
    @Override
    public void paint() {
        System.out.println("Renderizando uma caixa de seleção no estilo macOS.");
    }
}


// --- PASSO 3: Declare a interface da fábrica abstrata ---
// Ela deve ter métodos para criar TODOS os produtos abstratos (Button, Checkbox).

interface GUIFactory {
    Button createButton();
    Checkbox createCheckbox();
}


// --- PASSO 4: Implemente fábricas concretas (uma para cada variante) ---
// A fábrica para a variante Windows.

class WindowsFactory implements GUIFactory {
    @Override
    public Button createButton() {
        return new WindowsButton();
    }

    @Override
    public Checkbox createCheckbox() {
        return new WindowsCheckbox();
    }
}

// A fábrica para a variante macOS.
class MacOSFactory implements GUIFactory {
    @Override
    public Button createButton() {
        return new MacOSButton();
    }

    @Override
    public Checkbox createCheckbox() {
        return new MacOSCheckbox();
    }
}


// --- PASSO 5 e 6: O código cliente que usa a fábrica ---
// Esta classe (Application) não sabe qual FÁBRICA concreta ela está usando.
// Ela só sabe que tem uma FÁBRICA que pode criar botões e checkboxes.
// Isso atende ao PASSO 6: note que NÃO usamos "new WindowsButton()" aqui.

class Application {
    private Button button;
    private Checkbox checkbox;
    
    // A fábrica é injetada (passada) para a classe.
    public Application(GUIFactory factory) {
        // PASSO 6: Usamos o método de criação da fábrica, não o construtor direto.
        button = factory.createButton();
        checkbox = factory.createCheckbox();
    }

    public void paintUI() {
        button.paint();
        checkbox.paint();
    }
}

// --- PASSO 5: Código de inicialização da fábrica ---
// Este é o ponto de entrada que decide qual fábrica concreta usar.

public class DemoAbstractFactory {
    
    private static Application configureApplication() {
        GUIFactory factory;
        
        // Esta lógica decide qual família de produtos usar.
        // Poderia vir de um arquivo de configuração, variável de ambiente, etc.
        String osName = System.getProperty("os.name").toLowerCase();

        if (osName.contains("win")) {
            factory = new WindowsFactory();
        } else if (osName.contains("mac")) {
            factory = new MacOSFactory();
        } else {
            // Um fallback ou padrão
            System.out.println("OS não reconhecido, usando Windows como padrão.");
            factory = new WindowsFactory();
        }
        
        // A aplicação é criada com a fábrica selecionada.
        return new Application(factory);
    }

    public static void main(String[] args) {
        // O main apenas inicializa e executa.
        Application app = configureApplication();
        app.paintUI();
    }
}






```