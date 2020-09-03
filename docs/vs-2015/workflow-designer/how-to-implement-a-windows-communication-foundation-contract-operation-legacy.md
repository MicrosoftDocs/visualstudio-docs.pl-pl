---
title: 'Instrukcje: Implementowanie operacji Windows Communication Foundation Contract (starsza wersja) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1f6f54e781dfae15b4b1c1159d73ac3495b35c21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603865"
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>Instrukcje: Implementowanie operacji kontraktu usługi WCF (Windows Communication Foundation) (starsza wersja)
W tym temacie opisano sposób implementacji [!INCLUDE[indigo1](../includes/indigo1-md.md)] operacji kontraktu przy użyciu starszej wersji [!INCLUDE[wfd1](../includes/wfd1-md.md)] , która jest przeznaczona dla [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 Po przeciągnięciu działania **Receive** z przybornika do powierzchni projektowej przepływu pracy zostanie utworzony nowy [!INCLUDE[indigo2](../includes/indigo2-md.md)] kontrakt lub zaimportowano istniejący kontrakt i zaimplementowano operacje. Wybierasz i/lub tworzysz kontrakt oraz jego operacje za pomocą [okna dialogowego Wybieranie operacji (starsza wersja)](../workflow-designer/choose-operation-dialog-box-legacy.md).

### <a name="to-implement-a-wcf-contract-operation"></a>Aby zaimplementować operację kontraktu WCF

1. Kliknij dwukrotnie działanie **odbieranie** w projektancie lub kliknij wielokropek obok właściwości **we ServiceOperationInfo** w okienku **Właściwości** .

2. Wykonaj jedną z następujących czynności:

   - Kliknij przycisk **Dodaj kontrakt** w prawym górnym rogu okna dialogowego. Spowoduje to utworzenie nowego [!INCLUDE[indigo2](../includes/indigo2-md.md)] kontraktu i operacji.

      -lub-

   - Kliknij przycisk **Importuj** w prawym górnym rogu okna dialogowego. Zostanie otwarte okno [dialogowe Przeglądaj i wybierz typ platformy .NET (starsza wersja)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) . Wyszukaj zestaw lub projekt zawierający żądany kontrakt. Wybierz kontrakt, a następnie kliknij przycisk **OK**.

     Po utworzeniu lub zaimportowaniu kontraktu można dodać nowe operacje do tego utworzonego lub zaimportowanego kontraktu. Aby dodać nową operację, wybierz umowę, a następnie kliknij przycisk **Dodaj operację** w prawym górnym rogu okna dialogowego. Po zakończeniu dodawania operacji przejdź do kroku 3.

3. Wybierz operację, którą chcesz skojarzyć z działaniem **Receive** . Można manipulować definicją operacji, zmieniając nazwę, parametry, właściwości i ustawienia uprawnień operacji.

    Aby zmienić nazwę, wprowadź nową nazwę w polu tekstowym **nazwa operacji** .

    Kliknij kartę **Parametry** , aby uzyskać dostęp do parametrów operacji. Można zmienić nazwę, typ lub kierunek parametru oraz dodać lub usunąć parametry z operacji.

    Kliknij kartę **Właściwości** , aby uzyskać dostęp do poziomu ochrony operacji i obsługiwanej funkcji wymiany komunikatów.

    Kliknij kartę **uprawnienia** , aby określić, które grupy mogą zaimplementować operację.

4. Kliknięcie przycisku **OK** spowoduje wyświetlenie **w działaniu** nazwy operacji dla operacji implementującej.

5. Umieść działania przepływu pracy, które będą używane dla implementacji tej operacji w ramach działania **Receive** .

## <a name="see-also"></a>Zobacz też
 [Okno dialogowe Wybieranie operacji (starsza wersja)](../workflow-designer/choose-operation-dialog-box-legacy.md) [instrukcje: wywoływanie operacji kontraktu WCF (starsza wersja)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) [starsze działania przepływu pracy](../workflow-designer/legacy-workflow-activities.md)