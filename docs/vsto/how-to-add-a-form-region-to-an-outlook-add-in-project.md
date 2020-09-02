---
title: 'Instrukcje: Dodawanie regionu formularza do projektu dodatku programu Outlook'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VSTO.NewFormRegionWizard.Page1
- VSTO.NewFormRegionWizard.Page3
- VSTO.NewFormRegionWizard.Page2
- VSTO.NewFormRegionWizard.Page0
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], adding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a03ba05226720913d48dc1828dcb849bee72d17e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538401"
---
# <a name="how-to-add-a-form-region-to-an-outlook-add-in-project"></a>Instrukcje: Dodawanie regionu formularza do projektu dodatku programu Outlook
  Utwórz region formularza w celu rozbudowania standardowego lub niestandardowego formularza Microsoft Office Outlook przy użyciu **nowego kreatora regionu formularza programu Outlook** . Można utworzyć nowy region formularza i zaprojektować interfejs użytkownika w programie Visual Studio lub zaimportować region formularza, który został zaprojektowany w programie Outlook i dodać Visual Basic lub kod C#.

 Jeśli masz region formularza programu Outlook używany w innym projekcie programu Outlook, możesz użyć go ponownie w bieżącym projekcie dodatku VSTO programu Outlook przy użyciu okna dialogowego **Dodaj istniejący element** . Aby uzyskać więcej informacji, zobacz [Tworzenie regionów formularzy w programie Outlook](../vsto/creating-outlook-form-regions.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

### <a name="to-add-a-new-form-region-to-an-outlook-project"></a>Aby dodać nowy region formularza do projektu programu Outlook

1. Otwórz lub Utwórz projekt dodatku VSTO dla programu Outlook w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. W **Eksplorator rozwiązań**wybierz węzeł projekt dodatku VSTO programu Outlook.

3. W menu **projekt** kliknij polecenie **Dodaj nowy element**.

4. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **region formularza programu Outlook**.

5. Wpisz nazwę regionu formularza w polu **Nazwa** , a następnie kliknij przycisk **Dodaj**.

     Zostanie uruchomiony Kreator **regionu formularza NewOutlook** .

6. Na stronie **Wybierz, jak chcesz utworzyć region formularza** wybierz, czy chcesz zaprojektować region formularza, przeciągając formanty zarządzane do projektanta wizualnego, czy zaimportuj region formularza, który został zaprojektowany w programie Outlook.

    > [!NOTE]
    > W przypadku wybrania opcji importowania regionu formularza zaprojektowanego w programie Outlook należy określić lokalizację pliku magazynu formularza programu Outlook (*OFS*). Nie można dodać formantów zarządzanych do regionu formularza, który projektujesz w programie Outlook; można dodać tylko kod związany z istniejącym interfejsem użytkownika. Aby uzyskać więcej informacji, zobacz [Tworzenie regionów formularzy w programie Outlook](../vsto/creating-outlook-form-regions.md).

7. Na stronie **Wybierz typ regionu formularza, który chcesz utworzyć** , przejrzyj typy regionów formularzy i wybierz je, a następnie kliknij przycisk **dalej**. Aby uzyskać więcej informacji na temat typów regionów formularzy, zobacz [Tworzenie regionów formularzy w programie Outlook](../vsto/creating-outlook-form-regions.md).

8. Na stronie **Wprowadź tekst opisowy i wybierz stronę Preferencje wyświetlania** w polu **Nazwa** wpisz nazwę regionu formularza. W przypadku typów regionów zastępujących i Zamień wszystkie pola **tytuł** i **Opis** są również dostępne.

     Aby uzyskać informacje o tym, gdzie nazwa, tytuł i opis pojawiają się w programie Outlook podczas wdrażania regionu formularza, zobacz [Tworzenie regionów formularzy w programie Outlook](../vsto/creating-outlook-form-regions.md).

9. Wybierz co najmniej jeden tryb wyświetlania, w którym ma być wyświetlany region formularza.

     Wszystkie typy regionów formularza mogą pojawić się w inspektorach w trybie redagowania (na potrzeby tworzenia elementów) i w trybie odczytu (do wyświetlania elementów). Sąsiednie, zastępcze i Zamień — wszystkie typy regionów formularza mogą również być wyświetlane w okienku odczytywania.

10. Kliknij przycisk **Dalej**.

11. Na stronie **Zidentyfikuj klasy komunikatów, które będą wyświetlać ten region formularza** wybierz pozycję standardowe klasy wiadomości programu Outlook lub wpisz nazwy jednej lub kilku niestandardowych klas komunikatów, a następnie kliknij przycisk **Zakończ**. Aby uzyskać więcej informacji, zobacz [kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).

## <a name="see-also"></a>Zobacz też
- [Dostęp do regionu formularza w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md)
- [Rozwiązania programu Outlook](../vsto/outlook-solutions.md)
- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
- [Wytyczne dotyczące tworzenia regionów formularzy programu Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Przewodnik: Projektowanie regionu formularza programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Przewodnik: Importowanie regionów formularzy zaprojektowanych w programie Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Niestandardowe akcje w regionach formularzy programu Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
