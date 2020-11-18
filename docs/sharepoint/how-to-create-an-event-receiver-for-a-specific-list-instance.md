---
title: 'Instrukcje: Tworzenie odbiorcy zdarzeń dla określonego wystąpienia listy | Microsoft Docs'
titleSuffix: ''
description: Utwórz odbiorcę zdarzeń dla określonego wystąpienia listy. Odbiorca zdarzenia wystąpienia listy odpowiada na zdarzenia występujące w dowolnym wystąpieniu definicji listy.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8bd76f2aafc5d0b3058dcaba68b6f3099f01ff8d
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2020
ms.locfileid: "94849899"
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>Instrukcje: Tworzenie odbiorcy zdarzeń dla określonego wystąpienia listy
  Odbiorca zdarzenia wystąpienia listy odpowiada na zdarzenia występujące w dowolnym wystąpieniu definicji listy. Mimo że szablon odbiorcy zdarzeń nie umożliwia określania wartości docelowej określonego wystąpienia listy, można zmodyfikować odbiorcę zdarzeń, który jest objęty zakresem definicji listy w celu reagowania na zdarzenia w określonym wystąpieniu listy.

 Aby określić konkretne wystąpienie listy, w *Elements.xml* dla odbiorcy zdarzeń Zastąp wartość `ListTemplateId` `ListUrl` i Dodaj adres URL wystąpienia listy.

## <a name="create-a-list-instance-event-receiver"></a>Utwórz odbiorcę zdarzeń wystąpienia listy
 Poniższe kroki pokazują, jak zmodyfikować odbiorcę zdarzeń elementu listy w celu reagowania tylko na zdarzenia występujące w wystąpieniu listy anonsów niestandardowych.

#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>Aby zmodyfikować odbiorcę zdarzeń w celu reagowania na określone wystąpienie listy

1. W przeglądarce Otwórz witrynę programu SharePoint.

2. W okienku nawigacji **listy** łączy.

3. Na stronie **cała zawartość witryny** wybierz łącze **Utwórz** .

4. W oknie dialogowym **Tworzenie** wybierz typ **anonsów** , nazwij anons **TestAnnouncements**, a następnie wybierz przycisk **Utwórz** .

5. W programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Utwórz projekt odbiorcy zdarzeń.

6. Na liście żądany **Typ odbiorcy zdarzeń** wybierz pozycję **Wyświetl zdarzenia elementów**.

    > [!NOTE]
    > Możesz również wybrać dowolnego innego rodzaju odbiorcę zdarzeń, który ma zakresy do definicji listy, na przykład **listę zdarzeń poczty e-mail** lub **listę zdarzeń przepływu pracy**.

7. Na liście **element, który powinien być źródłem zdarzenia?** wybierz pozycję **Anonsy**.

8. Na liście **Obsługuj poniższe zdarzenia** zaznacz pole wyboru **element jest dodawany** , a następnie wybierz przycisk **Zakończ** .

9. W **Eksplorator rozwiązań** w obszarze EventReceiver1 Otwórz *Elements.xml*.

     Odbiorca zdarzeń odwołuje się obecnie do definicji listy anonsów, używając następującego wiersza:

    ```xml
    <Receivers ListTemplateId="104">
    ```

     Zmień ten wiersz na następujący tekst:

    ```xml
    <Receivers ListUrl="Lists/TestAnnouncements">
    ```

     Powoduje to skierowanie odbiornika zdarzeń do odpowiedzi tylko na zdarzenia występujące na nowej liście anonsów **TestAnnouncements** , która została właśnie utworzona. Można zmienić atrybut, `ListURL` Aby odwoływać się do dowolnego wystąpienia listy na serwerze programu SharePoint.

10. Otwórz plik kodu dla odbiorcy zdarzeń i umieść punkt przerwania w metodzie ItemAdding.

11. Wybierz klawisz **F5** , aby skompilować i uruchomić rozwiązanie.

12. W programie SharePoint wybierz łącze **TestAnnouncements** w okienku nawigacji.

13. Wybierz łącze **Dodaj nowe powiadomienie** .

14. Wprowadź tytuł anonsu, a następnie wybierz przycisk **Zapisz** .

     Należy zauważyć, że punkt przerwania jest trafień po dodaniu nowego elementu do listy anonsów niestandardowych.

15. Wybierz klawisz **F5** , który ma zostać wznowiony.

16. W okienku nawigacji wybierz łącze **listy** , a następnie wybierz łącze **Anonsy** .

17. Dodawanie nowego anonsu.

     Należy zauważyć, że odbiorca zdarzeń nie wyzwala nowego anonsu, ponieważ odbiornik jest skonfigurowany do odpowiadania tylko na zdarzenia w wystąpieniu listy anonsów niestandardowych, **TestAnnouncements**.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Tworzenie odbiorcy zdarzeń](../sharepoint/how-to-create-an-event-receiver.md)
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
