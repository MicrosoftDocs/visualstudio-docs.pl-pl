---
title: 'Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Word'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Word [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8aff32bbbbc396651079d16449e9746760c4541e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53856443"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-word"></a>Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Word
  Ten Przewodnik wprowadzający dowiesz się, jak utworzyć dostosowywania poziomie dokumentu dla programu Microsoft Office Word. Funkcje, które tworzysz w tego rodzaju rozwiązania są dostępne tylko wtedy, gdy określony dokument jest otwarty. Nie możesz użyć dostosowywania poziomie dokumentu do zmiany całej aplikacji, na przykład wyświetlanie Nowa karta wstążki, gdy dowolny dokument jest otwarty.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
- Tworzenie projektu dokumentu programu Word.  
  
- Dodawanie tekstu do dokumentu, który znajduje się w Projektancie Visual Studio.  
  
- Pisanie kodu, który używa modelu obiektów programu Word do dodawania tekstu dostosowany dokument po jego otwarciu.  
  
- Tworzenie i uruchamianie projektu, aby ją przetestować.  
  
- Czyszczenie projektu, aby usunąć z komputera dewelopera kompilacji niepotrzebne pliki i ustawienia zabezpieczeń.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="create-the-project"></a>Utwórz projekt  
  
### <a name="to-create-a-new-word-document-project-in-visual-studio"></a>Aby utworzyć nowy projekt dokumentu programu Word w programie Visual Studio  
  
1.  Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.  
  
3.  W okienku szablonów, rozwiń **Visual C#** lub **języka Visual Basic**, a następnie rozwiń węzeł **Office/SharePoint**.  
  
4.  W rozwiniętym okienku **Office/SharePoint** węzeł **dodatków pakietu Office** węzła.  
  
5.  Na liście szablonów projektu wybierz projekt dokument VSTO programu Word.  
  
6.  W **nazwa** wpisz **FirstDocumentCustomization**.  
  
7.  Kliknij przycisk **OK**.  
  
     **Visual Studio Tools dla pakietu Office, Kreator projektu** zostanie otwarty.  
  
8.  Wybierz **Utwórz nowy dokument**i kliknij przycisk **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tworzy **FirstDocumentCustomization** projektu i dodaje **FirstDocumentCustomization** ThisDocument plik kodu do projektu i dokumentów. **FirstDocumentCustomization** automatycznie otworzyć dokumentu w projektancie.  
  
## <a name="close-and-reopen-the-document-in-the-designer"></a>Zamknij i otwórz ponownie dokument w Projektancie  
 Jeśli celowo lub przypadkowo zamknięto dokumentu w Projektancie podczas tworzenia projektu, można otworzyć go ponownie.  
  
### <a name="to-close-and-reopen-the-document-in-the-designer"></a>Aby zamknąć i ponownie otworzyć dokument w Projektancie  
  
1.  Zamknij dokument, klikając przycisk **Zamknij** przycisku (X) dla okna projektanta.  
  
2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ThisDocument** plik kodu, a następnie kliknij przycisk **Projektant widoków**.  
  
     \- lub —  
  
     W **Eksploratora rozwiązań**, kliknij dwukrotnie **ThisDocument** pliku kodu.  
  
## <a name="add-text-to-the-document-in-the-designer"></a>Dodawanie tekstu do dokumentu w Projektancie  
 Interfejs użytkownika (UI) można zaprojektować swoje dostosowania, modyfikując dokument, który jest otwarty w projektancie. Na przykład można dodać tekst, tabele lub formanty programu Word. Aby uzyskać więcej informacji o sposobie korzystania z projektanta, zobacz [projekty pakietu Office w środowisku Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
### <a name="to-add-text-to-your-document-by-using-the-designer"></a>Aby dodać tekst w dokumencie przy użyciu narzędzia Projektant  
  
1.  W dokumencie, który jest otwarty w Projektancie wpisz następujący tekst.  
  
     **Ten tekst został dodany za pomocą projektanta.**  
  
## <a name="add-text-to-the-document-programmatically"></a>Programowe Dodawanie tekstu do dokumentu  
 Następnie dodaj kod do pliku kodu ThisDocument. Nowy kod używa modelu obiektów programu Word, można dodać drugi akapit tekstu do dokumentu. Domyślnie plik kodu ThisDocument zawiera następujące wygenerowanego kodu:  
  
-   Częściową definicję `ThisDocument` klasy, która reprezentuje model programowania dokumentu i zapewnia dostęp do modelu obiektów programu Word. Aby uzyskać więcej informacji, zobacz [element hosta dokumentu](../vsto/document-host-item.md) i [model obiektu Word — omówienie](../vsto/word-object-model-overview.md). W pozostałej części `ThisDocument` klasa jest zdefiniowana w pliku ukryty kod, który nie należy modyfikować.  
  
-   `ThisDocument_Startup` i `ThisDocument_Shutdown` procedury obsługi zdarzeń. Te procedury obsługi zdarzeń są wywoływane, gdy dokument jest otwarte i zamknięte. Użyj tych programów obsługi zdarzeń, zainicjować swoje dostosowania po otwarciu dokumentu, a także aby wyczyścić zasoby używane przez dostosowanie, gdy dokument zostanie zamknięty. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-a-second-paragraph-of-text-to-the-document-by-using-code"></a>Aby dodać drugi akapit w dokumencie przy użyciu kodu  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ThisDocument**, a następnie kliknij przycisk **Wyświetl kod**.  
  
     Otwiera plik kodu w programie Visual Studio.  
  
2.  Zastąp `ThisDocument_Startup` programu obsługi zdarzeń z następującym kodem. Po otwarciu dokumentu, ten kod dodaje drugi akapit tekstu do dokumentu.  
  
     [!code-vb[Trin_WordDocumentTutorial#1](../vsto/codesnippet/VisualBasic/FirstDocumentCustomization/ThisDocument.vb#1)]
     [!code-csharp[Trin_WordDocumentTutorial#1](../vsto/codesnippet/CSharp/FirstDocumentCustomization/ThisDocument.cs#1)]  
  
    > [!NOTE]  
    >  Ten kod używa wartości indeksu 1, aby dostęp do pierwszego akapitu w <xref:Microsoft.Office.Tools.Word.Document.Paragraphs%2A> właściwości. Chociaż Visual Basic i Visual C# należy używać tablic oparty na 0, niższe granice tablicy w większości kolekcji w modelu obiektów programu Word to 1. Aby uzyskać więcej informacji, zobacz [pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="test-the-project"></a>Projekt testowy  
  
### <a name="to-test-your-document"></a>Aby przetestować dokumentu  
  
1.  Naciśnij klawisz **F5** Aby skompilować i uruchomić projekt.  
  
     Gdy tworzysz projekt, kod jest kompilowany do zestawu, który jest skojarzony z dokumentem. Program Visual Studio umieszcza kopię dokumentu i zestawu w folderze danych wyjściowych kompilacji dla projektu i konfiguruje ustawienia zabezpieczeń na komputerze deweloperskim, aby włączyć dostosowywanie do uruchomienia. Aby uzyskać więcej informacji, zobacz [rozwiązań kompilacji pakietu Office](../vsto/building-office-solutions.md).  
  
2.  W tym dokumencie Sprawdź, czy zostanie wyświetlony następujący tekst.  
  
     **Ten tekst został dodany za pomocą projektanta.**  
  
     **Ten tekst został dodany przy użyciu kodu.**  
  
3.  Zamknij dokument.  
  
## <a name="clean-up-the-project"></a>Czyszczenie projektu  
 Po zakończeniu tworzenia projektu, należy usunąć pliki w folderze wyjściowym kompilacji i ustawienia zabezpieczeń utworzone w procesie kompilacji.  
  
### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Aby wyczyścić ukończone projektu na komputerze deweloperskim  
  
1.  W programie Visual Studio na **kompilacji** menu, kliknij przycisk **czyste rozwiązanie**.  
  
## <a name="next-steps"></a>Następne kroki  
 Teraz, po utworzeniu podstawowego dostosowywania poziomie dokumentu dla programu Word, można dowiedzieć się więcej o sposobie tworzenia dostosowań w tych tematach:  
  
-   Ogólne zadania programowania, które można wykonywać w dostosowaniach na poziomie dokumentu: [Program dostosowań poziomu dokumentu](../vsto/programming-document-level-customizations.md).  
  
-   Zadania związane z programowaniem, które są specyficzne dla dostosowywania poziomie dokumentu dla programu Word: [Word rozwiązania](../vsto/word-solutions.md).  
  
-   Za pomocą modelu obiektów programu Word: [Word — omówienie modelu obiektu](../vsto/word-object-model-overview.md).  
  
-   Dostosowywanie interfejsu użytkownika programu Word, na przykład dodawania niestandardowej karty do Wstążki lub tworząc własne okienko akcji: [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
-   Do wykonywania zadań, która nie jest możliwa za pomocą modelu obiektów programu Word (na przykład hostingu zarządzane formanty w dokumentach i powiązanie formanty programu Word z danymi przy użyciu danych Windows Forms przy użyciu rozszerzonych obiektów programu Word, dostarczone przez rozwiązań pakietu Office w Visual Studio Powiązanie modelu): [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md).  
  
-   Kompilowanie i debugowanie dostosowań poziomu dokumentu dla programu Word: [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md).  
  
-   Wdrażanie dostosowań poziomu dokumentu dla programu Word: [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Rozwiązania programu Word](../vsto/word-solutions.md)   
 [Program dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)   
 [Model obiektu Word — omówienie](../vsto/word-object-model-overview.md)   
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)   
 [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)   
 [Omówienie szablonów projektu pakietu Office](../vsto/office-project-templates-overview.md)  
