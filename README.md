# CifraCesar
static void Main(string[] args)
        {
            //Função que encripta cada letra com a chave passada
            char Cifra(char letra, int ch)
            {
                //Verifica se é um Caracter (letra) ou um Simbolo( !, @, #, etc ) ou um Espaço
                //Se não for um Caracter, sai do método e não executa o resto do método
                if (!char.IsLetter(letra))
                {
                    return letra;
                }
                
                return (char)((((letra + ch) - 65) % 26) + 65);
            }

            //Função que encripta a mensagem passada
            string Encriptar(string msg, int ch)
            {
                string saida = "";

                //Para cada letra da mensagem ele vai chamar a função Cifra()...
                foreach (char letra in msg)
                {
                    saida += Cifra(letra, ch);
                }

                return saida;
            }

            //Método para Decifrar a mensagem, chamando a função Encriptar
            string Decifrar(string msg, int ch)
            {
                return Encriptar(msg, 26 - ch);
            }


            string mensagem = "";
            string mensagemCifrada = "";
            int chave = 0;

            Console.WriteLine("Digite uma mensagem:");
            mensagem = Console.ReadLine();

            Console.WriteLine("Digite uma chave:");
            chave = Int32.Parse(Console.ReadLine());

            Console.WriteLine("Mensagem Cifrada:");
            mensagemCifrada = Encriptar(mensagem, chave);
            Console.WriteLine(mensagemCifrada);

            Console.WriteLine("Mensagem Decifrada:");
            string mensagemDecifrada = Decifrar(mensagemCifrada, chave);
            Console.WriteLine(mensagemDecifrada);

        }
