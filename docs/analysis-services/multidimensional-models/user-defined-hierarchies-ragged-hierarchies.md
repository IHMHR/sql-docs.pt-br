---
title: Hierarquias desbalanceadas | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4c5eb53a8ae3ff25b7c0b4d390d9c5ffc896e542
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="user-defined-hierarchies---ragged-hierarchies"></a>Hierarquias definidas pelo usuário - hierarquias desbalanceadas
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Uma hierarquia desbalanceada é uma hierarquia definida pelo usuário que tem um número irregular de níveis. Exemplos comuns incluem o organograma, onde um gerente de alto nível tem os gerentes departamentais e funcionários não gerentes como subordinados diretos, ou hierarquias geográficas constituídas de País-Região-Cidades, onde algumas cidades não têm um estado ou província pai, como Washington D.C., a Cidade do Vaticano ou Nova Délhi.  
  
 Na maioria das hierarquias em uma dimensão, cada nível tem o mesmo número de membros acima dele, como qualquer outro membro no mesmo nível. Uma hierarquia desbalanceada é diferente porque o pai lógico de pelo menos um membro não está no nível imediatamente acima do membro. Quando isso acontece, a hierarquia desce a níveis diferentes para caminhos de busca detalhada diferentes. Em um aplicativo cliente, isso pode tornar os caminhos de busca detalhada desnecessariamente complicados.  
  
 Os aplicativos cliente variam de acordo com a forma de tratamento de uma hierarquia desbalanceada. Se existirem hierarquias desbalanceadas em seu modelo, prepare-se para se empenhar ainda mais para obter o comportamento de renderização esperado.  
  
 A primeira etapa é verificar como o aplicativo cliente trata o caminho de busca detalhada. Por exemplo, o Excel repete os nomes pai como espaços reservados para valores ausentes. Para ver esse comportamento, crie uma Tabela Dinâmica usando a dimensão Sales Territory no modelo multidimensional do Adventure Works. Em uma Tabela Dinâmica que tem os atributos Group, Country e Region de Sales Territory, você verá que os países sem um valor de região obterão um espaço reservado; nesse caso, uma repetição do pai acima dele (nome do país). Esse comportamento deriva da propriedade da cadeia de conexão MDX Compatibility=1, que é fixa no Excel. Se o cliente não fornece naturalmente os comportamentos de busca detalhada buscados, você pode definir propriedades no modelo para alterar pelo menos alguns desses comportamentos.  
  
 Este tópico contém as seguintes seções:  
  
-   [Abordagens para modificar a navegação da busca detalhada em uma hierarquia desbalanceada](#bkmk_approach)  
  
-   [Definir HideMemberIf para ocultar membros em uma hierarquia regular](#bkmk_Hide)  
  
-   [Definir a compatibilidade MDX para determinar como espaços reservados são representados em aplicativos cliente](#bkmk_Mdx)  
  
##  <a name="bkmk_approach"></a> Abordagens para modificar a navegação da busca detalhada em uma hierarquia desbalanceada  
 A presença de uma hierarquia desbalanceada se torna um problema quando a navegação de busca detalhada não retorna valores esperados ou é percebida como inadequado para uso. Para corrigir problemas de navegação que resultam de hierarquias desbalanceadas, considere estas opções:  
  
-   Use uma hierarquia regular, mas defina a propriedade **HideMemberIf** em cada nível para especificar se um nível ausente é visualizado pelo usuário. Ao definir **HideMemberIf**, você também deve definir **MDXCompatibility** na cadeia de conexão para substituir comportamentos da navegação padrão. As instruções para definir essas propriedades são fornecidas neste tópico.  
  
-   Crie uma hierarquia pai-filho que gerencie explicitamente os membros de nível. Para obter uma ilustração da técnica, consulte [Hierarquia desbalanceada em SSAS (postagem de blog)](http://dwbi1.wordpress.com/2011/03/30/ragged-hierarchy-in-ssas/). Para obter mais informações nos Manuais Online, consulte [Dimensões pai-filho](../../analysis-services/multidimensional-models/parent-child-dimension.md). As desvantagens de criar uma hierarquia pai-filho são que você só pode ter uma por dimensão e, em geral, incorre em uma penalidade de desempenho ao calcular agregações para membros intermediários.  
  
 Se a dimensão contém mais de uma hierarquia desbalanceada, você deve usar a primeira abordagem, definindo **HideMemberIf**. Os desenvolvedores de BI com experiência prática no trabalho com hierarquias desbalanceadas defendem ainda mais as alterações adicionais nas tabelas de dados físicos, criando tabelas separadas para cada nível. Consulte [Martin Mason's the SSAS Financial Cube–Part 1a–Ragged Hierarchies (Cubo financeiro de SSAS de Martin Mason, Parte 1a, Hierarquias desbalanceadas) (blog)](http://martinmason.wordpress.com/2012/03/03/the-ssas-financial-cubepart-1aragged-hierarchies-cont/) para obter detalhes sobre essa técnica.  
  
##  <a name="bkmk_Hide"></a> Definir HideMemberIf para ocultar membros em uma hierarquia regular  
 Na tabela de uma dimensão imperfeita, os membros logicamente ausentes podem ser representados de formas diferentes. As células da tabela podem conter cadeias de caracteres nulas ou vazias ou podem conter o mesmo valor que o pai, servindo como espaço reservado. A representação de espaços reservados é determinada pelo status de espaço reservado dos membros filho, conforme determinado pela propriedade **HideMemberIf** e pela propriedade de cadeia de conexão **MDX Compatibility** do aplicativo cliente.  
  
 Para aplicativos cliente que oferecem suporte à exibição de hierarquias desbalanceadas, é possível usar essas propriedades para ocultar membros logicamente ausentes.  
  
1.  No SSDT, clique duas vezes em uma dimensão para abri-la no Designer de Dimensão. A primeira guia, Estrutura da Dimensão, mostra hierarquias de atributos no painel Hierarquias.  
  
2.  Clique com o botão direito do mouse em um membro na hierarquia e selecione **Propriedades**. Defina **HideMemberIf** com um dos valores descritos a seguir.  
  
    |Configuração de HideMemberIf|Description|  
    |--------------------------|-----------------|  
    |**Never**|Os membros do nível nunca são ocultos. Este é o valor padrão.|  
    |**OnlyChildWithNoName**|Um membro do nível ficará oculto quando for o único filho de seu pai e seu nome for uma cadeia de caracteres nula ou vazia.|  
    |**OnlyChildWithParentName**|Um membro do nível ficará oculto quando for o único filho de seu pai e seu for nome idêntico ao nome do pai.|  
    |**NoName**|Um membro do nível ficará oculto quando seu nome estiver vazio.|  
    |**ParentName**|Um membro do nível ficará oculto quando seu nome for idêntico ao de seu pai.|  
  
##  <a name="bkmk_Mdx"></a> Definir a compatibilidade MDX para determinar como espaços reservados são representados em aplicativos cliente  
 Após definir **HideMemberIf** em um nível de hierarquia, defina também a propriedade **MDX Compatibility** na cadeia de conexão enviada do aplicativo cliente. A definição **MDX Compatibility** determina se o **HideMemberIf** é usado.  
  
|Definição de MDX Compatibility|Description|Uso|  
|-------------------------------|-----------------|-----------|  
|**1**|Mostrar um valor de espaço reservado.|Esse é o padrão usado pelo Excel, pelo SSDT e pelo SSMS. Ele orienta o servidor a retornar valores de espaço reservado ao detalhar níveis vazios em uma hierarquia desbalanceada. Se você clicar no valor de espaço reservado, poderá continuar até obter os nós filho (folha)<br /><br /> O Excel tem a cadeia de conexão usada para conectar-se ao Analysis Services, e ele sempre define **MDX Compatibility** como 1 em cada nova conexão. Esse comportamento preserva a compatibilidade com versões anteriores.|  
|**2**|Oculte um valor de espaço reservado (um valor nulo ou uma duplicata do nível pai), mas mostre outros níveis e nós com valores relevantes.|**Compatibilidade MDX**=2 costuma ser visto como a configuração preferencial em termos de hierarquias desbalanceadas. Um relatório [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e alguns aplicativos cliente de terceiros talvez persistam nessa configuração.|  
  
## <a name="see-also"></a>Consulte também  
 [Criar hierarquias definidas pelo usuário](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)   
 [Hierarquias do usuário](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)   
 [Dimensões pai-filho](../../analysis-services/multidimensional-models/parent-child-dimension.md)   
 [Propriedades de cadeia de caracteres de Conexão & #40; Analysis Services & #41;](../../analysis-services/instances/connection-string-properties-analysis-services.md)  
  
  
