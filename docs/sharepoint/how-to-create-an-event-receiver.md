---
title: 'Instrukcje: Tworzenie odbiorcy zdarzeń | Microsoft Docs'
description: Utwórz odbiorcę zdarzeń, aby można było odpowiedzieć, gdy użytkownik współdziała z elementami programu SharePoint, takimi jak listy lub elementy listy.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 2e94bd1594f94f43c82eed5033d6ec2660905c18
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2020
ms.locfileid: "94849886"
---
# <a name="how-to-create-an-event-receiver"></a>Instrukcje: Tworzenie odbiorcy zdarzeń
  Tworząc *odbiorcy zdarzeń*, możesz odpowiedzieć, gdy użytkownik współdziała z elementami programu SharePoint, takimi jak listy lub elementy listy. Na przykład kod w odbiorcy zdarzeń może być wyzwalany, gdy użytkownik zmieni Kalendarz lub usunie nazwę z listy kontaktów. Postępując zgodnie z tym tematem, można dowiedzieć się, jak dodać odbiorcę zdarzeń do wystąpienia listy.

 Aby wykonać te czynności, musisz mieć zainstalowane [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i obsługiwane wersje systemu Windows i programu SharePoint. Ponieważ ten przykład wymaga projektu programu SharePoint, należy również wykonać procedurę opisaną w temacie [Przewodnik: Tworzenie kolumny witryny, typu zawartości i listy dla programu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).

## <a name="adding-an-event-receiver"></a>Dodawanie odbiorcy zdarzeń
 Projekt utworzony w [przewodniku: Tworzenie kolumny witryny, typu zawartości i listy dla programu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) zawiera niestandardowe kolumny witryny, listę niestandardową i typ zawartości. Poniższa procedura umożliwia rozwinięcie tego projektu przez dodanie prostego programu obsługi zdarzeń (odbiorcy zdarzeń) do wystąpienia listy w celu pokazania sposobu obsługi zdarzeń występujących w elementach programu SharePoint, takich jak listy.

#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>Aby dodać odbiorcę zdarzeń do wystąpienia listy

1. Otwórz projekt, który został utworzony w [przewodniku: Tworzenie kolumny witryny, typu zawartości i listy dla programu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).

2. W **Eksplorator rozwiązań** wybierz węzeł projektu programu SharePoint o nazwie **Klinika**.

3. Na pasku menu wybierz **projekt**  >  **Dodaj nowy element**.

4. W obszarze **Visual C#** lub **Visual Basic** rozwiń węzeł **SharePoint** , a następnie wybierz element **2010** .

5. W okienku **Szablony** wybierz pozycję **Odbiorca zdarzenia**, nadaj jej nazwę **TestEventReceiver1**, a następnie wybierz przycisk **OK** .

     Zostanie wyświetlony **Kreator dostosowania programu SharePoint** .

6. Na liście żądany **Typ odbiorcy zdarzeń** wybierz pozycję **Wyświetl zdarzenia elementów**.

7. Na liście **element, który powinien być źródłem zdarzenia?** wybierz pozycję **pacjenci (Clinic\Patients)**.

8. Na liście **Obsługuj poniższe zdarzenia** zaznacz pole wyboru obok **elementu**, a następnie wybierz przycisk **Zakończ** .

     Plik kodu dla nowego odbiorcy zdarzeń zawiera pojedynczą metodę o nazwie `ItemAdded` . W następnym kroku dodasz kod do tej metody, aby każdy kontakt miał domyślnie nazwę Scott Brown.

9. Zastąp istniejącą `ItemAdded` metodę poniższym kodem, a następnie wybierz klawisz **F5** :

     [!code-csharp[SP_EventReceiver#1](../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]

     Kod zostanie uruchomiony, a witryna programu SharePoint zostanie wyświetlona w przeglądarce sieci Web.

10. Na pasku szybkiego uruchamiania wybierz łącze **pacjentów** , a następnie wybierz link **Dodaj nowy element** .

     Zostanie otwarty formularz wprowadzania dla nowych elementów.

11. Wprowadź dane w polach, a następnie wybierz przycisk **Zapisz** .

     Po wybraniu przycisku **Zapisz** kolumna **Nazwa pacjenta** zostanie automatycznie zaktualizowana do nazwy Scott Brown.

## <a name="see-also"></a>Zobacz także

- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)