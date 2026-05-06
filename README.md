# Painel-Logistico
meu primeiro site
export default function LogisticsDashboard() {
  const sections = {
    home: {
      title: 'Painel de Gestão Logística - Visão Geral',
      content: 'Selecione uma opção no painel para visualizar os módulos do sistema.'
    },
    novaSaida: {
      title: 'Registrar Nova Saída',
      content: 'Tela responsável pelo registro de saída de produtos do estoque.'
    },
    triagem: {
      title: 'Triagem e Conferência',
      content: 'Área para conferência de mercadorias recebidas e identificação de divergências.'
    },
    lancamento: {
      title: 'Lançamento de Dados',
      content: 'Cadastro e atualização de produtos, fornecedores e movimentações.'
    },
    inventario: {
      title: 'Visualizar Inventário',
      content: 'Dashboard completo com estoque disponível, gráficos e movimentações.'
    },
    nfe: {
      title: 'Consultar NF-e',
      content: 'Consulta detalhada de notas fiscais eletrônicas e download de XML.'
    },
    mensagens: {
      title: 'Atendimento Integrado',
      content: 'Sistema interno de mensagens corporativas e suporte operacional.'
    },
    receita: {
      title: 'Fontes de Receita',
      content: 'Análises financeiras, gráficos de lucro e desempenho operacional.'
    }
  };

  const [activeSection, setActiveSection] = React.useState('home');

  const renderContent = () => {
    switch (activeSection) {
      case 'novaSaida':
        return (
          <div className="space-y-4">
            <div className="grid grid-cols-2 gap-4">
              <input className="bg-purple-950 border border-purple-500 rounded-xl p-3" placeholder="Produto" />
              <input className="bg-purple-950 border border-purple-500 rounded-xl p-3" placeholder="Código do Produto" />
              <input className="bg-purple-950 border border-purple-500 rounded-xl p-3" placeholder="Quantidade" />
              <input className="bg-purple-950 border border-purple-500 rounded-xl p-3" placeholder="Responsável" />
            </div>
            <textarea className="w-full bg-purple-950 border border-purple-500 rounded-xl p-3 h-32" placeholder="Observações" />
            <div className="flex gap-3">
              <button className="bg-purple-500 hover:bg-purple-400 px-5 py-3 rounded-xl">Confirmar Saída</button>
              <button className="bg-white/10 hover:bg-white/20 px-5 py-3 rounded-xl">Gerar Comprovante</button>
            </div>
          </div>
        );

      case 'triagem':
        return (
          <div className="space-y-4">
            <table className="w-full bg-purple-950 rounded-2xl overflow-hidden">
              <thead className="bg-purple-700">
                <tr>
                  <th className="p-3 text-left">Produto</th>
                  <th className="p-3 text-left">Quantidade</th>
                  <th className="p-3 text-left">Status</th>
                </tr>
              </thead>
              <tbody>
                <tr className="border-t border-purple-800">
                  <td className="p-3">Monitor LG 24</td>
                  <td className="p-3">10</td>
                  <td className="p-3 text-green-400">Conferido</td>
                </tr>
                <tr className="border-t border-purple-800">
                  <td className="p-3">Mouse Logitech</td>
                  <td className="p-3">15</td>
                  <td className="p-3 text-yellow-400">Divergência</td>
                </tr>
              </tbody>
            </table>
          </div>
        );

      case 'inventario':
        return (
          <div className="space-y-6">
            <div className="grid grid-cols-3 gap-4">
              <div className="bg-purple-950 p-5 rounded-2xl">
                <h3 className="text-sm opacity-70">Produtos em Estoque</h3>
                <p className="text-3xl font-bold mt-2">1.240</p>
              </div>
              <div className="bg-purple-950 p-5 rounded-2xl">
                <h3 className="text-sm opacity-70">Itens Baixos</h3>
                <p className="text-3xl font-bold mt-2 text-red-400">12</p>
              </div>
              <div className="bg-purple-950 p-5 rounded-2xl">
                <h3 className="text-sm opacity-70">Entradas Hoje</h3>
                <p className="text-3xl font-bold mt-2">58</p>
              </div>
            </div>
            <div className="bg-purple-950 rounded-2xl p-5 h-64 flex items-center justify-center text-purple-300">
              Área de gráficos e métricas do inventário
            </div>
          </div>
        );

      case 'mensagens':
        return (
          <div className="grid grid-cols-3 gap-4 h-[500px]">
            <div className="bg-purple-950 rounded-2xl p-4 space-y-3">
              <div className="bg-purple-800 p-3 rounded-xl cursor-pointer hover:bg-purple-700">
                Financeiro
              </div>
              <div className="bg-purple-800 p-3 rounded-xl cursor-pointer hover:bg-purple-700">
                Estoque
              </div>
              <div className="bg-purple-800 p-3 rounded-xl cursor-pointer hover:bg-purple-700">
                Transportadora
              </div>
            </div>

            <div className="col-span-2 bg-purple-950 rounded-2xl flex flex-col">
              <div className="border-b border-purple-800 p-4 font-bold text-lg">
                Chat Corporativo
              </div>

              <div className="flex-1 p-4 space-y-4 overflow-auto">
                <div className="bg-purple-800 p-3 rounded-2xl max-w-md">
                  Bom dia, a nota fiscal 45892 apresentou divergência no frete.
                </div>

                <div className="bg-purple-500 p-3 rounded-2xl max-w-md ml-auto">
                  Estamos verificando junto ao setor logístico.
                </div>

                <div className="bg-purple-800 p-3 rounded-2xl max-w-md">
                  Preciso da correção ainda hoje para liberar o pagamento.
                </div>
              </div>

              <div className="border-t border-purple-800 p-4 flex gap-3">
                <input
                  className="flex-1 bg-black/30 rounded-xl px-4 py-3"
                  placeholder="Digite uma mensagem..."
                />
                <button className="bg-purple-500 hover:bg-purple-400 px-6 rounded-xl">
                  Enviar
                </button>
              </div>
            </div>
          </div>
        );

      default:
        return (
          <div className="bg-purple-950 rounded-2xl p-8 text-center text-purple-200">
            <h2 className="text-3xl font-bold mb-3">{sections[activeSection].title}</h2>
            <p>{sections[activeSection].content}</p>
          </div>
        );
    }
  };

  return (
    <div className="min-h-screen bg-gradient-to-br from-[#14011f] via-[#2d0a4f] to-[#100018] text-white p-6 font-sans">
      <div className="max-w-7xl mx-auto">
        <div className="bg-black/20 backdrop-blur-md rounded-3xl border border-purple-700 shadow-2xl overflow-hidden">
          <div className="bg-gradient-to-r from-purple-900 to-purple-700 px-8 py-6 border-b border-purple-500">
            <h1 className="text-4xl font-black tracking-wide text-center">
              PAINEL DE GESTÃO LOGÍSTICA
            </h1>
            <p className="text-center text-purple-200 mt-2">
              Sistema Integrado de Controle Operacional
            </p>
          </div>

          <div className="grid grid-cols-4 gap-4 p-6">
            <div className="bg-purple-900/60 rounded-2xl p-5 space-y-4 hover:scale-[1.01] transition-all">
              <h2 className="font-bold text-xl">Entrada & Saída</h2>

              <button
                onClick={() => setActiveSection('novaSaida')}
                className="w-full bg-purple-500 hover:bg-purple-400 p-3 rounded-xl transition"
              >
                Nova Saída
              </button>

              <button
                onClick={() => setActiveSection('triagem')}
                className="w-full bg-white/10 hover:bg-white/20 p-3 rounded-xl transition"
              >
                Triagem e Conferência
              </button>

              <button
                onClick={() => setActiveSection('lancamento')}
                className="w-full bg-white/10 hover:bg-white/20 p-3 rounded-xl transition"
              >
                Lançamento de Dados
              </button>
            </div>

            <div className="bg-purple-900/60 rounded-2xl p-5 space-y-4 hover:scale-[1.01] transition-all">
              <h2 className="font-bold text-xl">Controle de Estoque</h2>

              <button
                onClick={() => setActiveSection('inventario')}
                className="w-full bg-purple-500 hover:bg-purple-400 p-3 rounded-xl transition"
              >
                Visualizar Inventário
              </button>

              <div className="space-y-2 text-sm text-purple-200">
                <div className="flex justify-between">
                  <span>Item 01</span>
                  <span>45%</span>
                </div>
                <div className="h-2 bg-black/30 rounded-full overflow-hidden">
                  <div className="h-full w-[45%] bg-purple-400"></div>
                </div>
              </div>
            </div>

            <div className="bg-purple-900/60 rounded-2xl p-5 space-y-4 hover:scale-[1.01] transition-all">
              <h2 className="font-bold text-xl">Atendimento</h2>

              <button
                onClick={() => setActiveSection('mensagens')}
                className="w-full bg-purple-500 hover:bg-purple-400 p-3 rounded-xl transition"
              >
                Enviar Mensagem
              </button>

              <div className="bg-black/20 p-4 rounded-2xl space-y-2 text-sm">
                <div className="bg-purple-800 p-2 rounded-lg w-fit">
                  Olá, preciso de suporte.
                </div>
                <div className="bg-purple-500 p-2 rounded-lg w-fit ml-auto">
                  Estamos verificando.
                </div>
              </div>
            </div>

            <div className="bg-purple-900/60 rounded-2xl p-5 space-y-4 hover:scale-[1.01] transition-all">
              <h2 className="font-bold text-xl">Financeiro</h2>

              <button
                onClick={() => setActiveSection('nfe')}
                className="w-full bg-purple-500 hover:bg-purple-400 p-3 rounded-xl transition"
              >
                Consultar NF-e
              </button>

              <button
                onClick={() => setActiveSection('receita')}
                className="w-full bg-white/10 hover:bg-white/20 p-3 rounded-xl transition"
              >
                Fontes de Receita
              </button>

              <div className="bg-black/20 rounded-2xl h-32 flex items-center justify-center text-purple-300 text-sm">
                Área de gráficos financeiros
              </div>
            </div>
          </div>

          <div className="p-6 border-t border-purple-800 bg-black/20 min-h-[420px]">
            <h2 className="text-3xl font-bold mb-6">
              {sections[activeSection].title}
            </h2>

            {renderContent()}
          </div>
        </div>
      </div>
    </div>
  );
}
