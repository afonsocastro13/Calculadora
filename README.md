import java.util.Scanner

fun main() {
    val scanner = Scanner(System.`in`)
    println("=== CALCULADORA EM KOTLIN ===")

    while (true) {
        println("\nInsere a operação no formato: número operador número (ex: 4 + 5)")
        print("Ou escreve 'sair' para terminar: ")

        val input = scanner.nextLine()
        if (input.lowercase() == "sair") {
            println("A sair da calculadora. Até breve!")
            break
        }

        try {
            val partes = input.split(" ")
            if (partes.size != 3) {
                println("❌ Formato inválido. Usa o formato: número operador número")
                continue
            }

            val num1 = partes[0].toDouble()
            val operador = partes[1]
            val num2 = partes[2].toDouble()
            val resultado = when (operador) {
                "+" -> num1 + num2
                "-" -> num1 - num2
                "*" -> num1 * num2
                "/" -> {
                    if (num2 == 0.0) {
                        println("❌ Erro: divisão por zero.")
                        continue
                    } else num1 / num2
                }
                else -> {
                    println("❌ Operador inválido. Usa +, -, * ou /.")
                    continue
                }
            }

            println("✅ Resultado: $num1 $operador $num2 = $resultado")

        } catch (e: Exception) {
            println("❌ Erro ao processar a operação: ${e.message}")
        }
    }
}
