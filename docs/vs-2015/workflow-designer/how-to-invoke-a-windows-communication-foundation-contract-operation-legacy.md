---
title: 'Instrukcje: Wywoływanie Windows Communication Foundation operacji kontraktu usługi WCF (starsza wersja) | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d42c9698c6d3a247601909909c49fa92d2d29978
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60056669"
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Instrukcje: Wywoływanie operacji kontraktu usługi WCF (Windows Communication Foundation) (starsza wersja)
W tym temacie opisano, jak wywołać [!INCLUDE[indigo1](../includes/indigo1-md.md)] kontrakt operacji za pomocą starszego [!INCLUDE[wfd1](../includes/wfd1-md.md)] przeznaczonego [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Po przeciągnięciu **SendActivity** działania z przybornika do powierzchni projektu przepływu pracy, musisz zaimportować istniejący kontrakt i określić, która operacja zostanie wywołany przy jego użyciu **SendActivity** działanie. Zaznacz kontrakt usługi i jego operacji za pośrednictwem [wybierz operację okno dialogowe (starsza wersja)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
 Ponadto korzystania z plików konfiguracji przy użyciu usługi należy określić <xref:System.Workflow.Activities.ChannelToken>. <xref:System.Workflow.Activities.ChannelToken> Identyfikuje konfiguracji punktu końcowego działania wysyłania będzie używana do łączenia usługi przepływu pracy.  
  
### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>Do wywołania operacji kontraktu usługi WCF z działania SendActivity  
  
1. Kliknij dwukrotnie **SendActivity** działania w Projektancie lub kliknij wielokropek obok pozycji **właściwości ServiceOperationInfo** właściwość **właściwości** okienka.  
  
2. Gdy **wybierz operację** zostanie otwarte okno dialogowe, kliknij przycisk **importu** w prawym górnym rogu okna dialogowego.  
  
     [Wyszukaj i wybierz .NET typu, okno dialogowe (starsza wersja)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) zostanie otwarty.  
  
3. Wyszukaj zestaw lub projekt, który zawiera kontrakt, który chcesz.  
  
4. Wybierz umowę, a następnie kliknij przycisk **OK**.  
  
5. W obszarze **dostępne operacje**, wybrać operację, aby wywołać, a następnie kliknij przycisk **OK**.  
  
### <a name="to-specify-a-channel-token"></a>Aby określić token kanału  
  
1. Wybierz <xref:System.Workflow.Activities.SendActivity> działania w projektancie.  
  
2. W **właściwości** okienko, określ nazwę <xref:System.Workflow.Activities.ChannelToken>. Ta nazwa jest jednoznacznie identyfikuje tokenu kanału.  
  
3. Rozwiń węzeł tokenu kanału i określ nazwę dla punktu końcowego klienta, które zamierzasz używać w <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A> pola. Konfiguracja punktu końcowego o takiej samej nazwie w pliku konfiguracji będzie służyć do konfigurowania kanału.  
  
4. Tworzenie konfiguracji punktu końcowego w pliku konfiguracji, jeśli go jeszcze nie istnieje. Aby uzyskać więcej informacji na temat konfigurowania klienta, zobacz [Przegląd klienta programu WCF](http://msdn.microsoft.com/library/f60d9bc5-8ade-4471-8ecf-5a07a936c82d).  
  
## <a name="see-also"></a>Zobacz też  
 [Wybierz operację, okno dialogowe (starsza wersja)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Instrukcje: Implementowanie operacji kontraktu usługi WCF (starsza wersja)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Działania przepływu pracy w starszej wersji](../workflow-designer/legacy-workflow-activities.md)