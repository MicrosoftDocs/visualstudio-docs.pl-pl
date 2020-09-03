---
title: 'Instrukcje: Tworzenie aplikacji usługi przepływu pracy WCF | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9bf941babd943c6856809a13de847b62745b2056
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72605010"
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>Instrukcje: Tworzenie aplikacji usługi przepływu pracy WCF
[!INCLUDE[indigo1](../includes/indigo1-md.md)] aplikacje usługi przepływu pracy są rozproszonymi usługami komunikacyjnymi, które przechodzą komunikaty między klientami i w różnych granicach procesu. Wdrożenie kontraktu usługi po stronie usługi jest wykonywane w sposób deklaratywny przez działania przepływu pracy w systemie [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] w sposób analogiczny do starszych usług przepływu pracy w .NET Framework 3,5.

### <a name="to-create-a-wcf-workflow-service-application"></a>Aby utworzyć aplikację usługi przepływu pracy WCF

1. Rozpocznij [!INCLUDE[vs2010](../includes/vs2010-md.md)] .

2. W menu **plik** wskaż polecenie **Nowy**, a następnie wybierz pozycję **projekt...**.

     Zostanie otwarte okno dialogowe **Nowy projekt** .

3. W okienku **zainstalowane szablony** wybierz opcję **WCF** lub **przepływ pracy** z grup **Visual C#** lub **Visual Basic** w zależności od wybranego języka.

4. W środkowym okienku wybierz pozycję **aplikacja usługi przepływu pracy WCF**.

5. W polu **Nazwa** Wprowadź opisową nazwę projektu, aby ułatwić jego identyfikację.

6. W polu **Lokalizacja** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** , aby przejść do niego.

7. W polu **rozwiązanie** wybierz opcję utworzenia nowego rozwiązania, a następnie kliknij przycisk **OK**.

    > [!NOTE]
    > Jeśli chcesz dodać aplikację konsoli przepływu pracy do istniejącego rozwiązania, Otwórz to rozwiązanie w programie, kliknij [!INCLUDE[vs2010](../includes/vs2010-md.md)] prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań**i wybierz polecenie **Dodaj**, a następnie **Nowy projekt...** Aby otworzyć okno dialogowe **Nowy projekt** . Postępuj zgodnie z powyższym opisem w tej procedurze.

8. Szablon projektu tworzy definicję usługi jako XAML. [!INCLUDE[wfd1](../includes/wfd1-md.md)]Zostanie otwarty widok Projekt z <xref:System.Activities.Statements.Sequence> działaniem zawierającym zestaw <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działania.

## <a name="see-also"></a>Zobacz też
 [Instrukcje: tworzenie działania](https://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436) [tworzenia projektu przepływu pracy](../workflow-designer/creating-a-workflow-project.md)