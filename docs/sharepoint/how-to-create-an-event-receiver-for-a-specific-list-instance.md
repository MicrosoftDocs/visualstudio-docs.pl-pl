---
title: 'Instrukcje: Tworzenie obsługiwanego odbiornika dla określonej listy formularzy | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 615b9bc4974a0483dec5e9c39727ebae50039a1f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596532"
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>Instrukcje: Tworzenie obsługiwanego odbiornika dla określonej listy formularzy
  Odbiornik zdarzeń wystąpienia listy reaguje na zdarzenia występujące w żadnym wystąpieniu definicji listy. Choć szablonu odbiorcy zdarzenia nie przeznaczonych dla określonej listy formularzy, możesz zmodyfikować odbiorcy zdarzeń, które są ograniczone do definicji listy w celu reagowania na zdarzenia w określonej listy formularzy.

 Pod kątem określonej listy formularzy w *Elements.xml* odbiorcy zdarzeń można zastąpić `ListTemplateId` z `ListUrl` i Dodaj adres URL wystąpienia listy.

## <a name="create-a-list-instance-event-receiver"></a>Utwórz odbiornik zdarzeń wystąpienia listy
 Poniższe kroki pokazują sposób modyfikowania odbiorca zdarzenia elementu listy, ma odpowiadać tylko na zdarzenia występujące w wystąpieniu Niestandardowa lista anonsów.

#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>Aby zmodyfikować odbiorcy zdarzenia i reagować na określonej listy formularzy

1.  W przeglądarce otwórz witrynę programu SharePoint.

2.  W okienku nawigacji **Wyświetla** łącza.

3.  W **całą zawartość lokacji** wybierz **Utwórz** łącza.

4.  W **Utwórz** okna dialogowego wybierz **anonsów** wpisz, określ nazwę anonsu **TestAnnouncements**, a następnie wybierz **Utwórz**przycisku.

5.  W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], Utwórz projekt odbiorcy zdarzeń.

6.  W **jakiego typu odbiorcę zdarzeń chcesz wykonać?** wybierz **zdarzenia elementu listy**.

    > [!NOTE]
    >  Możesz również wybrać dowolny inny rodzaj odbiorcy zdarzeń, który zakresów w definicji listy, na przykład **listę zdarzeń poczty E-mail** lub **zdarzenia przepływu pracy listy**.

7.  W **jaki element ma być źródła zdarzeń?** wybierz **anonsów**.

8.  W **obsługę następujących zdarzeń** listy wybierz **zostanie dodany element** pole wyboru, a następnie wybierz **Zakończ** przycisku.

9. W **Eksploratora rozwiązań**, w obszarze EventReceiver1, otwórz *Elements.xml*.

     Odbiorcy zdarzeń obecnie odwołuje się do definicji listy ogłoszeń przy użyciu następujący wiersz:

    ```xml
    <Receivers ListTemplateId="104">
    ```

     Zmień ten wiersz do następującego tekstu:

    ```xml
    <Receivers ListUrl="Lists/TestAnnouncements">
    ```

     Spowoduje to nieprzekazywanie odbiorcy zdarzeń ma odpowiadać tylko na zdarzenia występujące w nowym **TestAnnouncements** Lista anonsów, który został utworzony. Możesz zmienić `ListURL` atrybutu, aby odwoływać się do dowolnego wystąpienia listy na serwerze programu SharePoint.

10. Otwórz plik kodu dla odbiorcy zdarzeń i umieść punkt przerwania w metodzie ItemAdding.

11. Wybierz **F5** klawisz, aby skompilować i uruchomić rozwiązanie.

12. W programie SharePoint, wybierz **TestAnnouncements** łącze w okienku nawigacji.

13. Wybierz **Dodaj nowy anons** łącza.

14. Wprowadź tytuł powiadomienia, a następnie wybierz **Zapisz** przycisku.

     Należy zauważyć, że punkt przerwania zostaje trafiony, gdy nowy element zostanie dodany do listy niestandardowej anonsów.

15. Wybierz **F5** klawisz, aby wznowić.

16. W okienku nawigacji wybierz **Wyświetla** łącze, a następnie wybierz **anonsów** łącza.

17. Dodaj nowe zawiadomienie.

     Należy zauważyć, że odbiorca zdarzenia nie będzie wyzwalać na nowy anons odbiornika skonfigurowano brane są tylko zdarzenia w wystąpienia listy niestandardowej anonsu, **TestAnnouncements**.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Tworzenie obsługiwanego odbiornika](../sharepoint/how-to-create-an-event-receiver.md)
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
