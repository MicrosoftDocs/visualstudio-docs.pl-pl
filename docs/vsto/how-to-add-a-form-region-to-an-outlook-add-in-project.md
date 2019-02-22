---
title: 'Instrukcje: Dodawanie regionu formularza do projektu dodatku programu Outlook'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 97d8883ef22fc91b708726fddca60cf757e3d9a8
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56610622"
---
# <a name="how-to-add-a-form-region-to-an-outlook-add-in-project"></a>Instrukcje: Dodawanie regionu formularza do projektu dodatku programu Outlook
  Tworzenie regionu formularza, aby rozszerzyć standardowy lub niestandardowy formularz programu Microsoft Office Outlook za pomocą **nowy Region formularza programu Outlook** kreatora. Możesz utworzyć nowy region formularza i projektowanie interfejsu użytkownika w programie Visual Studio lub można importować regionu formularza zaprojektowanego w programie Outlook i Dodaj języka Visual Basic lub C# kodu.

 W przypadku regionów formularzy programu Outlook, które było używane w innym projekcie programu Outlook może używać go w bieżącym projekcie dodatku narzędzi VSTO dla programu Outlook przy użyciu **Dodaj istniejący element** okno dialogowe. Aby uzyskać więcej informacji, zobacz [regionach formularzy programu Outlook z tworzenia](../vsto/creating-outlook-form-regions.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

### <a name="to-add-a-new-form-region-to-an-outlook-project"></a>Aby dodać nowy region formularza do projektu programu Outlook

1.  Otwórz lub Utwórz projekt dodatku narzędzi VSTO dla programu Outlook w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2.  W **Eksploratora rozwiązań**, wybierz węzeł projektu dodatku narzędzi VSTO dla programu Outlook.

3.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.

4.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **Region formularza programu Outlook**.

5.  Wpisz nazwę dla regionu formularza w **nazwa** , a następnie kliknij przycisk **Dodaj**.

     **Regionu formularza NewOutlook** uruchamiany jest Kreator.

6.  Na **wybierz sposób tworzenia regionu formularza** wybierz, czy chcesz zaprojektować regionu formularza za pomocą przeciągania zarządzane formanty do projektanta wizualnego lub zaimportować regionu formularza zaprojektowanego w programie Outlook.

    > [!NOTE]
    >  Jeśli decydujesz się zaimportować regionu formularza zaprojektowanego w programie Outlook, a następnie należy określić lokalizację magazynu formularzy programu Outlook (*OFS*) pliku. Nie można dodać zarządzane formanty do regionu formularza, który projektowania w programie Outlook; można dodać tylko kod związany z istniejącego interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [regionach formularzy programu Outlook z tworzenia](../vsto/creating-outlook-form-regions.md).

7.  Na **wybierz typ regionu formularza chcesz utworzyć** strony, przejrzyj typów regionu formularza i wybierz jedną, a następnie kliknij **dalej**. Aby uzyskać więcej informacji na temat typów regionu formularza, zobacz [regionach formularzy programu Outlook z tworzenia](../vsto/creating-outlook-form-regions.md).

8.  Na **tekst opisu i wybierz preferencje wyświetlania** stronie **nazwa** wpisz nazwę dla regionu formularza. Zastąpienie i typów regionów formularza Zamień wszystkie **tytuł** i **opis** pola również są dostępne.

     Aby dowiedzieć się, jak gdzie nazwę, tytuł i opis są wyświetlane w programie Outlook w przypadku wdrażania regionu formularza, zobacz [regionach formularzy programu Outlook z tworzenia](../vsto/creating-outlook-form-regions.md).

9. Wybierz co najmniej jeden trybów wyświetlania, w których ma być wyświetlane regionu formularza.

     Wszystkie typy regionu formularza może występować w inspektorów, w trybie redagowania (do tworzenia elementów) i w trybie do odczytu (w przypadku wyświetlania elementów). Sąsiadujące, zamieniania i typów regionów formularza Zamień wszystkie również może znajdować się w okienku odczytu.

10. Kliknij przycisk **Dalej**.

11. Na **Określ klasy wiadomości, które będzie wyświetlany ten region formularza** stronie, wybierz standardowych klas wiadomości programu Outlook lub wpisz nazwy co najmniej jedną klasę niestandardową wiadomość, a następnie kliknij **Zakończ**. Aby uzyskać więcej informacji, zobacz [kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).

## <a name="see-also"></a>Zobacz także
- [Dostęp do regionów formularzy w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md)
- [Rozwiązania programu Outlook](../vsto/outlook-solutions.md)
- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
- [Wytyczne dotyczące tworzenia regionów formularzy programu Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Przewodnik: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Przewodnik: Importowanie regionów formularzy zaprojektowanych w programie Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Niestandardowe akcje w regionach formularzy programu Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
