Factory Method
// Interfaz del producto
public interface ITransporte {
    void Entregar();
}

// Clases concretas
public class Camion : ITransporte {
    public void Entregar() => Console.WriteLine("Entrega en camión.");
}

public class Barco : ITransporte {
    public void Entregar() => Console.WriteLine("Entrega en barco.");
}

// Fábrica
public abstract class Logistica {
    public abstract ITransporte CrearTransporte();
}

public class LogisticaTerrestre : Logistica {
    public override ITransporte CrearTransporte() => new Camion();
}

public class LogisticaMaritima : Logistica {
    public override ITransporte CrearTransporte() => new Barco();
}

// Uso
class Program {
    static void Main() {
        Logistica logistica = new LogisticaTerrestre();
        ITransporte transporte = logistica.CrearTransporte();
        transporte.Entregar();
    }
}

Singleton
public class Singleton {
    private static Singleton instancia;
    private static readonly object lockObj = new object();

    private Singleton() { }

    public static Singleton Instancia {
        get {
            lock (lockObj) {
                if (instancia == null)
                    instancia = new Singleton();
            }
            return instancia;
        }
    }
}

