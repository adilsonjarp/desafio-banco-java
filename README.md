// Classe Cliente
public class Cliente {
    private String nome;
    private String cpf;
    
    // Construtor, getters e setters
}

// Classe Conta
public abstract class Conta {
    protected Cliente cliente;
    protected double saldo;

    public Conta(Cliente cliente) {
        this.cliente = cliente;
        this.saldo = 0.0;
    }

    public void depositar(double valor) {
        this.saldo += valor;
    }

    public void sacar(double valor) {
        if (this.saldo >= valor) {
            this.saldo -= valor;
        } else {
            System.out.println("Saldo insuficiente");
        }
    }

    public double getSaldo() {
        return saldo;
    }

    public abstract void imprimirExtrato();
}

// Classe ContaCorrente
public class ContaCorrente extends Conta {
    public ContaCorrente(Cliente cliente) {
        super(cliente);
    }

    @Override
    public void imprimirExtrato() {
        System.out.println("=== Extrato Conta Corrente ===");
        System.out.println("Cliente: " + cliente.getNome());
        System.out.println("Saldo: " + saldo);
    }
}

// Classe ContaPoupanca
public class ContaPoupanca extends Conta {
    public ContaPoupanca(Cliente cliente) {
        super(cliente);
    }

    @Override
    public void imprimirExtrato() {
        System.out.println("=== Extrato Conta Poupança ===");
        System.out.println("Cliente: " + cliente.getNome());
        System.out.println("Saldo: " + saldo);
    }
}
