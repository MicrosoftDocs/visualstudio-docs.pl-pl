---
title: 'Instrukcje: wywoływanie operacji kontraktu Windows Communication Foundation (starsza wersja) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6f42600a739561a27a6dd8f6caa237027bac4554
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603703"
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Instrukcje: wywoływanie operacji kontraktu Windows Communication Foundation (starsza wersja)
W tym temacie opisano sposób wywoływania operacji [!INCLUDE[indigo1](../includes/indigo1-md.md)] kontraktu przy użyciu starszej [!INCLUDE[wfd1](../includes/wfd1-md.md)], która jest przeznaczona dla [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Po przeciągnięciu działania **wysyłania** z przybornika do powierzchni projektowej przepływu pracy należy zaimportować istniejący kontrakt i określić, która operacja zostanie wywołana z tego działania **wysyłania** . Kontrakt i jego operacje są wybierane za pomocą [okna dialogowego Wybieranie operacji (starsza wersja)](../workflow-designer/choose-operation-dialog-box-legacy.md).

 Ponadto, jeśli używasz pliku konfiguracji z usługą, musisz określić <xref:System.Workflow.Activities.ChannelToken>. @No__t_0 identyfikuje konfigurację punktu końcowego, która będzie używana do nawiązywania połączenia z usługą przepływu pracy.

### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>Aby wywołać operację kontraktu WCF z działania wysyłania

1. Kliknij dwukrotnie działanie **send** w projektancie lub kliknij wielokropek obok właściwości **we ServiceOperationInfo** w okienku **Właściwości** .

2. Gdy zostanie otwarte okno dialogowe **Wybieranie operacji** , kliknij przycisk **Importuj** w prawym górnym rogu okna dialogowego.

     Zostanie otwarte okno [dialogowe Przeglądaj i wybierz typ platformy .NET (starsza wersja)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) .

3. Wyszukaj zestaw lub projekt zawierający żądany kontrakt.

4. Wybierz kontrakt, a następnie kliknij przycisk **OK**.

5. W obszarze **dostępne operacje**wybierz operację, którą chcesz wywołać, a następnie kliknij przycisk **OK**.

### <a name="to-specify-a-channel-token"></a>Aby określić token kanału

1. Wybierz działanie <xref:System.Workflow.Activities.SendActivity> w projektancie.

2. W okienku **Właściwości** określ nazwę <xref:System.Workflow.Activities.ChannelToken>. Ta nazwa jednoznacznie identyfikuje token kanału.

3. Rozwiń węzeł token kanału i określ nazwę punktu końcowego klienta, który ma być używany w polu <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A>. Konfiguracja punktu końcowego o tej samej nazwie w pliku konfiguracji zostanie użyta do skonfigurowania kanału.

4. Utwórz konfigurację punktu końcowego w pliku konfiguracji, jeśli jeszcze nie istnieje. Aby uzyskać więcej informacji na temat konfigurowania klienta, zobacz [Omówienie klienta programu WCF](https://msdn.microsoft.com/library/f60d9bc5-8ade-4471-8ecf-5a07a936c82d).

## <a name="see-also"></a>Zobacz też
 [Okno dialogowe Wybieranie operacji (starsza wersja)](../workflow-designer/choose-operation-dialog-box-legacy.md) [instrukcje: Implementowanie operacji kontraktu WCF (starsza wersja)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) [starszych działań przepływu pracy](../workflow-designer/legacy-workflow-activities.md)