---
title: sysmergearticles (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sysmergearticles
- sysmergearticles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmergearticles system table
ms.assetid: e9b1648e-4660-4688-9f56-18b2baf7228c
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: f20b8c4793f43be53fb8d2efaadf49a4d7e71025
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="sysmergearticles-transact-sql"></a>sysmergearticles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contém uma linha para cada artigo de mesclagem definido no banco de dados local. Essa tabela é armazenada no banco de dados de publicação.  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nome do artigo.|  
|**type**|**tinyint**|Indica o tipo do artigo, que pode ser um dos seguintes:<br /><br /> **10** = tabela.<br /><br /> **32** = procedimento armazenado (somente esquema).<br /><br /> **64** = exibição ou (somente esquema) da exibição indexada.<br /><br /> **128** = função definida pelo usuário (somente esquema).<br /><br /> **160** = sinônimo (somente esquema).|  
|**objid**|**Int**|O identificador de objeto.|  
|**sync_objid**|**Int**|A ID de objeto da exibição que representa o conjunto de dados sincronizado.|  
|**view_type**|**tinyint**|O tipo da exibição.<br /><br /> **0** = não uma exibição; use todos os objetos base.<br /><br /> **1** = exibição permanente.<br /><br /> **2** = exibição temporária.|  
|**artid**|**uniqueidentifier**|O número de identificação exclusivo para o artigo determinado.|  
|**Descrição**|**nvarchar(255)**|A descrição breve do artigo.|  
|**pre_creation_command**|**tinyint**|A ação padrão a ser tomada quando o artigo é criado no banco de dados de assinatura:<br /><br /> **0 =** nenhum - se a tabela já existir no assinante, nenhuma ação será tomada.<br /><br /> **1** = descartar - descarta a tabela antes de criá-lo novamente.<br /><br /> **2** = excluir-emite uma exclusão com base na cláusula WHERE no filtro de subconjunto.<br /><br /> **3** = truncar-igual **2**, mas exclui páginas em vez de linhas. Porém, não exige uma cláusula WHERE.|  
|**pubid**|**uniqueidentifier**|A ID da publicação à qual o artigo atual pertence.|  
|**Apelido**|**Int**|O mapeamento de apelido para identificação do artigo.|  
|**column_tracking**|**Int**|Indica se o controle de coluna é implementado para o artigo.|  
|**status**|**tinyint**|Indica o status do artigo, que pode ser um dos seguintes:<br /><br /> **1** = não sincronizado - o script de processamento inicial para publicar a tabela será executado na próxima vez em que o Snapshot Agent é executado.<br /><br /> **2** = ativo - o script de processamento inicial para publicar a tabela foi executado.<br /><br /> **5** = New_inactive - a ser adicionado.<br /><br /> **6** = New_active - a ser adicionado.|  
|**conflict_table**|**sysname**|O nome da tabela local que contém os registros conflitantes para o artigo atual. Essa tabela é somente informativa e seu conteúdo pode ser modificado ou excluído por rotinas de resolução de conflitos personalizadas ou diretamente pelo administrador.|  
|**creation_script**|**nvarchar(255)**|O script de criação para este artigo.|  
|**conflict_script**|**nvarchar(255)**|O script de conflito para este artigo.|  
|**article_resolver**|**nvarchar(255)**|O resolvedor de conflitos personalizado de nível de linha para este artigo.|  
|**ins_conflict_proc**|**sysname**|O procedimento usado para gravar conflitos em **conflict_table**.|  
|**insert_proc**|**sysname**|O procedimento usado pelo resolvedor de conflitos padrão para inserir linhas durante a sincronização.|  
|**update_proc**|**sysname**|O procedimento usado pelo resolvedor de conflitos padrão para atualizar linhas durante a sincronização.|  
|**select_proc**|**sysname**|O nome de um procedimento armazenado gerado automaticamente usado pelo Merge Agent para efetuar bloqueio e localizar colunas e linhas para um artigo.|  
|**metadata_select_proc**|**sysname**|O nome do procedimento armazenado gerado automaticamente usado para acessar metadados nas tabelas do sistema de replicação de mesclagem.|  
|**delete_proc**|**sysname**|O procedimento usado pelo resolvedor de conflitos padrão para excluir linhas durante a sincronização.|  
|**schema_option**|**binary(8)**|Para obter os valores com suporte de *schema_option*, consulte [sp_addmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md).|  
|**destination_object**|**sysname**|O nome da tabela criada no Assinante.|  
|**destination_owner**|**sysname**|O nome do proprietário do objeto de destino.|  
|**resolver_clsid**|**nvarchar(50)**|A ID do resolvedor de conflitos personalizado.|  
|**subset_filterclause**|**nvarchar(1000)**|A cláusula de filtro para este artigo.|  
|**missing_col_count**|**Int**|O número de colunas ausentes.|  
|**missing_cols**|**varbinary(128)**|O bitmap de colunas ausentes.|  
|**excluded_cols**|**varbinary(128)**|O bitmap das colunas excluídas do artigo quando é enviado ao Assinante.|  
|**excluded_col_count**|**Int**|O número de colunas excluídas.|  
|**columns**|**varbinary(128)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**deleted_cols**|**varbinary(128)**|Os bitmaps de colunas que foram excluídas da tabela de origem.|  
|**resolver_info**|**nvarchar(255)**|O armazenamento de informações adicionais requeridas por resolvedores de conflitos personalizados.|  
|**view_sel_proc**|**nvarchar(290)**|O nome de um procedimento armazenado que o Merge Agent usa para popular inicialmente um artigo em uma publicação filtrada dinamicamente e para enumerar linhas alteradas em qualquer publicação filtrada.|  
|**gen_cur**|**Int**|O número gerado de alterações locais para a tabela base de um artigo.|  
|**vertical_partition**|**Int**|Especifica se a filtragem de coluna está habilitada em um artigo de tabela. **0** indica que não há filtragem vertical e publica todas as colunas.|  
|**identity_support**|**Int**|Especifica se o tratamento de intervalo de identidade automático está habilitado. **1** significa que a manipulação de intervalo de identidade é habilitada, e **0** significa que não há nenhuma identidade de intervalo de suporte.|  
|**before_image_objid**|**Int**|A ID de objeto da tabela de controle. A tabela de controle contém certos valores de coluna de chave quando uma publicação é criada com *@keep_partition_changes*  =  **true**.|  
|**before_view_objid**|**Int**|A ID de objeto de uma tabela de exibição. A exibição está em uma tabela que controla se uma linha pertenceu a um Assinante específico antes de ser excluída ou atualizada. Aplica-se apenas quando uma publicação é criada com *@keep_partition_changes*  =  **true.**|  
|**verify_resolver_signature**|**Int**|Especifica se uma assinatura digital é verificada antes de usar um resolvedor em replicação de mesclagem:<br /><br /> **0** = assinatura não for verificada.<br /><br /> **1** = assinatura é verificada para ver se ele é de uma fonte confiável.|  
|**allow_interactive_resolver**|**bit**|Especifica se o uso do Resolvedor Interativo em um artigo está habilitado. **1** Especifica que o resolvedor interativo é usado no artigo.|  
|**fast_multicol_updateproc**|**bit**|Especifica se o Merge Agent foi habilitado para aplicar alterações em várias colunas na mesma linha em uma instrução UPDATE.<br /><br /> **0** = problemas de uma atualização separada para cada coluna alterada.<br /><br /> **1** = emite uma instrução UPDATE que faz com que as atualizações ocorram em várias colunas em uma instrução.|  
|**check_permissions**|**Int**|O bitmap das permissões no nível de tabela que são verificadas quando o Merge Agent aplica alterações no Publicador. *check_permissions* pode ter um destes valores:<br /><br /> **0x00 =** permissões não são verificadas.<br /><br /> **0x10 =** verifica permissões no publicador antes que INSERTs feitas no assinante sejam carregadas.<br /><br /> **0x20 =** verifica permissões no publicador antes que as atualizações feitas no assinante sejam carregadas.<br /><br /> **0x40 =** verifica permissões no publicador antes que DELETEs feitas no assinante sejam carregadas.|  
|**maxversion_at_cleanup**|**Int**|A geração mais alta para a qual os metadados são limpos.|  
|**processing_order**|**Int**|Indica a ordem de processamento de artigos em uma publicação de mesclagem; onde um valor de **0** indica que o artigo está classificado e artigos são processados na ordem do valor mais baixo para o mais alto. Se dois artigos tiverem o mesmo valor, serão processados simultaneamente. Para obter mais informações, consulte [Especificar a ordem de processamento dos artigos de mesclagem](../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md).|  
|**upload_options**|**tinyint**|Define restrições em atualizações feitas em um Assinante com uma assinatura de cliente, que pode ser um dos valores a seguir.<br /><br /> **0** = não existem restrições em atualizações feitas em um assinante com assinatura de cliente; todas as alterações são carregadas no publicador.<br /><br /> **1** = as alterações são permitidas em um assinante com assinatura de cliente, mas eles não são carregados no publicador.<br /><br /> **2** = não são permitidas alterações em um assinante com assinatura de cliente.<br /><br /> Para obter mais informações, consulte [Optimize Merge Replication Performance with Download-Only Articles](../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md) (Otimizar o desempenho da replicação de mesclagem com artigos somente para download).|  
|**published_in_tran_pub**|**bit**|Indica que um artigo em uma publicação de mesclagem também é publicado em uma publicação transacional.<br /><br /> **0** = o artigo não é publicado em um artigo transacional.<br /><br /> **1** = o artigo também é publicado em um artigo transacional.|  
|**lightweight**|**bit**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**procname_postfix**|**nchar(32)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**well_partitioned_lightweight**|**bit**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**before_upd_view_objid**|**Int**|A ser adicionado.|  
|**delete_tracking**|**bit**|Indica se as exclusões são replicadas.<br /><br /> **0** = exclusões não são replicadas.<br /><br /> **1** = as exclusões são replicadas, que é o comportamento padrão para replicação de mesclagem.<br /><br /> Quando o valor de *delete_tracking* é **0**, linhas excluídas no assinante devem ser removidas manualmente no publicador e linhas excluídas no publicador devem ser removidas manualmente no assinante.<br /><br /> Observação: Um valor de **0** resulta em não convergência.|  
|**compensate_for_errors**|**bit**|Indica se ações compensatórias são tomadas quando são encontrados erros durante a sincronização.<br /><br /> **0** = Compensating ações estão desabilitadas.<br /><br /> **1** = alterações que não podem ser aplicadas em um assinante ou publicador sempre conduzem a ações de compensação para desfazer essas alterações, que é o comportamento padrão para replicação de mesclagem.<br /><br /> Observação: Um valor de **0** resulta em não convergência.|  
|**pub_range**|**bigint**|O tamanho do intervalo de identidade do publicador.|  
|**range**|**bigint**|O tamanho dos valores de identidade consecutivos que seria atribuído a assinantes em um ajuste.|  
|**threshold**|**Int**|A porcentagem de limite do intervalo de identidade.|  
|**stream_blob_columns**|**bit**|Especifica se uma otimização de fluxo de dados é usada ao replicar colunas de objeto binário grande. **1** significa que a otimização é tentada.|  
|**preserve_rowguidcol**|**bit**|Indica se replicação usa uma coluna rowguid existente. Um valor de **1** significa que uma coluna ROWGUIDCOL existente é usada. **0** significa que a replicação adicionou a coluna ROWGUIDCOL.|  
  
## <a name="see-also"></a>Consulte também  
 [Tabelas de replicação &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Exibições de replicação &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_addmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)   
 [sp_changemergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)   
 [sp_helpmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md)  
  
  
