---
title: 'Instrukcje: Tworzenie obsługiwanego odbiornika | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.EventReceiver
dev_langs:
- VB
- CSharp
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
ms.openlocfilehash: bc42a92e1d7dcc73bb6bc0433da4e6a31d7fefb2
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60081963"
---
# <a name="how-to-create-an-event-receiver"></a>Instrukcje: Tworzenie obsługiwanego odbiornika
  Tworząc *odbiorcy zdarzeń*, mogą odpowiadać, gdy użytkownik korzysta z elementów programu SharePoint, takich jak listy lub elementów listy. Na przykład kod w odbiorcy zdarzeń mogą być wyzwalane, gdy użytkownik zmienia kalendarza lub usuwa nazwę z listy kontaktów. Korzystając z tego tematu, można poznać sposoby dodawania odbiorców zdarzenia do wystąpienia listy.

 Aby wykonać te kroki, musisz zainstalować [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i obsługiwane wersje systemu Windows i programu SharePoint. Ponieważ w tym przykładzie wymaga projektu programu SharePoint, należy również wykonać procedurę opisaną w temacie [instruktażu: Tworzenie kolumny witryny, typu zawartości oraz list dla SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).

## <a name="adding-an-event-receiver"></a>Dodanie odbiorcy zdarzeń
 Projekt, który został utworzony w [instruktażu: Tworzenie kolumny witryny, typu zawartości oraz list dla SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) zawiera kolumny niestandardowej witryny, listy niestandardowej i typu zawartości. W poniższej procedurze będzie rozwinąć tego projektu, dodając procedurę obsługi zdarzenia prostego (odbiorca zdarzenia) do wystąpienia listy, aby pokazać sposób obsługi zdarzeń występujących w elementach programu SharePoint, takich jak listy.

#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>Aby dodać odbiorca zdarzenia do wystąpienia listy

1. Otwórz projekt, który został utworzony w [instruktażu: Tworzenie kolumny witryny, typu zawartości oraz list dla SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).

2. W **Eksploratora rozwiązań**, wybierz węzeł projektu programu SharePoint, która nosi nazwę **Clinic**.

3. Na pasku menu wybierz **projektu** > **Dodaj nowy element**.

4. W obszarze **Visual C#** lub **języka Visual Basic**, rozwiń węzeł **SharePoint** węzła, a następnie wybierz **2010** elementu.

5. W **szablony** okienku wybierz **odbiorcy zdarzeń**, nadaj jej nazwę **TestEventReceiver1**, a następnie wybierz **OK** przycisku.

     **Kreator ustawień niestandardowych SharePoint** pojawia się.

6. W **jakiego typu odbiorcę zdarzeń chcesz wykonać?** wybierz **zdarzenia elementu listy**.

7. W **jaki element ma być źródła zdarzeń?** wybierz **pacjentów (Clinic\Patients)**.

8. W **obsługę następujących zdarzeń** listy, zaznacz pole wyboru obok pozycji **dodano element**, a następnie wybierz **Zakończ** przycisku.

     Plik kodu dla nowego odbiorcę zdarzeń zawiera jedną metodę o nazwie `ItemAdded`. W następnym kroku dodasz kod do tej metody, aby każdy kontakt będzie miała Scott Brown domyślnie.

9. Zastąp istniejące `ItemAdded` metody za pomocą następujących kodu, a następnie wybierz **F5** klucza:

     [!code-csharp[SP_EventReceiver#1](../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]

     Uruchamia kod, a witryna jest wyświetlana w przeglądarce sieci web programu SharePoint.

10. Na pasku szybkiego uruchamiania wybierz **pacjentów** łącze, a następnie wybierz **Dodaj nowy element** łącza.

     Zostanie otwarty formularz wprowadzania dla nowych elementów.

11. Wprowadź dane w polach, a następnie wybierz **Zapisz** przycisku.

     Po wybraniu **Zapisz** przycisku **nazwa pacjenta** kolumny automatycznie aktualizuje nazwę Scott Brown.

## <a name="see-also"></a>Zobacz także

- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)