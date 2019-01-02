---
title: 'Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Word'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Word [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f8cd238c64b32501a42900d37723c350e84673f1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53948975"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-word"></a>Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Word
  Ten Przewodnik wprowadzający przedstawia sposób tworzenia dodatku narzędzi VSTO dla programu Microsoft Office Word. Funkcje, które tworzysz w tego rodzaju rozwiązania są dostępne dla aplikacji, niezależnie od tego, które są otwarte dokumenty.  
  
 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
- Tworzenie projektu dodatku narzędzi VSTO programu Word.  
  
- Pisanie kodu, który używa modelu obiektów programu Word do dodawania tekstu do dokumentu, podczas zapisywania.  
  
- Tworzenie i uruchamianie projektu, aby ją przetestować.  
  
- Czyszczenie zakończone projektu tak, aby dodatku narzędzi VSTO już nie uruchamia automatycznie na komputerze deweloperskim.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="create-the-project"></a>Utwórz projekt  
  
### <a name="to-create-a-new-word-vsto-add-in-project-in-visual-studio"></a>Aby utworzyć nowy projekt dodatku narzędzi VSTO programu Word w programie Visual Studio  
  
1.  Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.  
  
3.  W okienku szablonów, rozwiń **Visual C#** lub **języka Visual Basic**, a następnie rozwiń węzeł **Office/SharePoint**.  
  
4.  W rozwiniętym okienku **Office/SharePoint** węzeł **dodatków pakietu Office** węzła.  
  
5.  Na liście szablonów projektu wybierz projekt dodatku narzędzi VSTO programu Word.  
  
6.  W **nazwa** wpisz **FirstWordAddIn**.  
  
7.  Kliknij przycisk **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tworzy **FirstWordAddIn** projektu i otwiera plik kodu ThisAddIn w edytorze.  
  
## <a name="write-code-to-add-text-to-the-saved-document"></a>Pisanie kodu, aby dodać tekst zapisany dokument  
 Następnie dodaj kod, aby plik kodu ThisAddIn. Nowy kod używa modelu obiektów programu Word, aby dodawać standardowy tekst do każdego zapisany dokument. Domyślnie plik kodu ThisAddIn zawiera następujące wygenerowanego kodu:  
  
-   Częściową definicję `ThisAddIn` klasy. Ta klasa udostępnia punkt wejścia dla kodu i zapewnia dostęp do modelu obiektów programu Word. Aby uzyskać więcej informacji, zobacz [dodatków narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md). W pozostałej części `ThisAddIn` klasa jest zdefiniowana w pliku ukryty kod, który nie należy modyfikować.  
  
-   `ThisAddIn_Startup` i `ThisAddIn_Shutdown` procedury obsługi zdarzeń. Te procedury obsługi zdarzeń są wywoływane, gdy wyraz ładuje i zwalnia dodatku narzędzi VSTO dla programów. Użyj tych programów obsługi zdarzeń, można zainicjować dodatku narzędzi VSTO dla programów, podczas jego ładowania oraz aby wyczyścić zasoby używane przez dodatek narzędzi VSTO dla programu, gdy jest zwolniony. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-a-paragraph-of-text-to-the-saved-document"></a>Aby dodać akapit tekstu do zapisanego dokumentu  
  
1. W pliku kodu ThisAddIn, Dodaj następujący kod do `ThisAddIn` klasy. Nowy kod definiuje zdarzenia obsługi dla <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> zdarzenie, które jest wywoływane, gdy dokument zostanie zapisany.  
  
    Gdy użytkownik zapisuje dokument, program obsługi zdarzeń dodaje nowy tekst na początku dokumentu.  
  
    [!code-vb[Trin_WordAddInTutorial#1](../vsto/codesnippet/VisualBasic/FirstWordAddIn/ThisAddIn.vb#1)]
    [!code-csharp[Trin_WordAddInTutorial#1](../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs#1)]  
  
   > [!NOTE]  
   >  Ten kod zawiera wartość indeksu, od 1 do dostępu do pierwszego akapitu w <xref:Microsoft.Office.Interop.Word._Document.Paragraphs%2A> kolekcji. Chociaż Visual Basic i Visual C# należy używać tablic oparty na 0, niższe granice tablicy w większości kolekcji w modelu obiektów programu Word to 1. Aby uzyskać więcej informacji, zobacz [pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md).  
  
2. Jeśli używasz języka C#, Dodaj następujący kod wymagany do `ThisAddIn_Startup` programu obsługi zdarzeń. Ten kod służy do łączenia `Application_DocumentBeforeSave` programu obsługi zdarzeń z <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> zdarzeń.  
  
    [!code-csharp[Trin_WordAddInTutorial#2](../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs#2)]  
  
   Do modyfikacji dokumentu po jego zapisaniu, w poprzednich przykładach kodu za pomocą następujących obiektów:  
  
-   `Application` Pole `ThisAddIn` klasy. `Application` Pole zwraca <xref:Microsoft.Office.Interop.Word.Application> reprezentujący bieżące wystąpienie programu Word.  
  
-   `Doc` Parametrów programu obsługi zdarzeń <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> zdarzeń. `Doc` Parametr <xref:Microsoft.Office.Interop.Word.Document> obiektu, który reprezentuje zapisany dokument. Aby uzyskać więcej informacji, zobacz [model obiektu Word — omówienie](../vsto/word-object-model-overview.md).  
  
## <a name="test-the-project"></a>Projekt testowy  
  
### <a name="to-test-the-project"></a>Aby przetestować projekt  
  
1.  Naciśnij klawisz **F5** Aby skompilować i uruchomić projekt.  
  
     Gdy tworzysz projekt, kod jest kompilowany do zestawu, który znajduje się w folderze wyjściowym kompilacji dla projektu. Visual Studio tworzy również zestaw wpisów rejestru, umożliwiające Word wykrycie i załadowanie dodatku narzędzi VSTO dla programów i konfiguruje ustawienia zabezpieczeń na komputerze deweloperskim, aby włączyć dodatek narzędzi VSTO dla programów do uruchomienia. Aby uzyskać więcej informacji, zobacz [rozwiązań kompilacji pakietu Office](../vsto/building-office-solutions.md).  
  
2.  W programie Word zapisz aktywny dokument.  
  
3.  Sprawdź, czy następujący tekst został dodany do dokumentu.  
  
     **Ten tekst został dodany przy użyciu kodu.**  
  
4.  Zamknij program Word.  
  
## <a name="clean-up-the-project"></a>Czyszczenie projektu  
 Po zakończeniu tworzenia projektu dodatku narzędzi VSTO zestaw, wpisy rejestru i ustawienia zabezpieczeń należy usunąć z komputera dewelopera. W przeciwnym razie dodatku narzędzi VSTO będzie każdym razem, Otwórz program Word na komputerze deweloperskim.  
  
### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Aby wyczyścić ukończone projektu na komputerze deweloperskim  
  
1.  W programie Visual Studio na **kompilacji** menu, kliknij przycisk **czyste rozwiązanie**.  
  
## <a name="next-steps"></a>Następne kroki  
 Teraz, gdy utworzono podstawowe dodatku narzędzi VSTO dla programu Word, można dowiedzieć się więcej o tworzeniu dodatków narzędzi VSTO dla programów w tych tematach:  
  
-   Ogólne zadań programistycznych, które można wykonywać w dodatkach VSTO: [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Zadania programowania, które są specyficzne dla dodatków narzędzi VSTO programu Word: [Word rozwiązania](../vsto/word-solutions.md).  
  
-   Za pomocą modelu obiektów programu Word: [Word — omówienie modelu obiektu](../vsto/word-object-model-overview.md).  
  
-   Dostosowywanie interfejsu użytkownika programu Word, na przykład przez dodawanie kart niestandardowych do Wstążki lub tworzenia własnego niestandardowego okienka zadań: [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
-   Kompilowanie i debugowanie dodatków narzędzi VSTO dla programu Word: [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md).  
  
-   Wdrażanie dodatków narzędzi VSTO dla programu Word: [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Rozwiązania programu Word](../vsto/word-solutions.md)   
 [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Model obiektu Word — omówienie](../vsto/word-object-model-overview.md)   
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)   
 [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)   
 [Omówienie szablonów projektu pakietu Office](../vsto/office-project-templates-overview.md)  
