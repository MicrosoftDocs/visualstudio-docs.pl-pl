---
title: 'Przewodnik: tworzenie pierwszego dodatku VSTO dla programu Word'
description: Utwórz dodatek na poziomie aplikacji dla programu Microsoft Word. Ta funkcja jest dostępna dla samej aplikacji, niezależnie od tego, które dokumenty są otwarte.
ms.custom: SEO-VS-2020
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fd3509ab674faa220ed7bbea15a9762f52b1a525
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828283"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-word"></a>Przewodnik: tworzenie pierwszego dodatku VSTO dla programu Word
  W tym przewodniku wprowadzającym pokazano, jak utworzyć dodatek VSTO dla programu Microsoft Office Word. Funkcje, które tworzysz w tego typu rozwiązaniu, są dostępne dla samej aplikacji, niezależnie od tego, które dokumenty są otwarte.

 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie projektu dodatku Word VSTO.

- Pisanie kodu, który używa modelu obiektów programu Word w celu dodania tekstu do dokumentu po jego zapisaniu.

- Budowania i uruchamiania projektu w celu przetestowania go.

- Czyszczenie ukończonego projektu tak, aby dodatek VSTO nie był już automatycznie uruchamiany na komputerze dewelopera.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Tworzenie projektu

### <a name="to-create-a-new-word-vsto-add-in-project-in-visual-studio"></a>Aby utworzyć nowy projekt dodatku Word VSTO w programie Visual Studio

1. Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. W menu **File (Plik)** wskaż pozycję **New (Nowy),** a następnie kliknij pozycję **Project (Projekt).**

3. W okienku szablonów rozwiń pozycję **Visual C#** **lub Visual Basic**, a następnie rozwiń pozycję **Office/SharePoint.**

4. W rozwiniętym **węźle Office/SharePoint** wybierz węzeł Dodatki **pakietu Office.**

5. Na liście szablonów projektów wybierz projekt dodatku Word VSTO.

6. W polu **Nazwa** wpisz **FirstWordAddIn**.

7. Kliknij przycisk **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tworzy projekt **FirstWordAddIn** i otwiera plik kodu ThisAddIn w edytorze.

## <a name="write-code-to-add-text-to-the-saved-document"></a>Pisanie kodu w celu dodania tekstu do zapisanego dokumentu
 Następnie dodaj kod do pliku kodu ThisAddIn. Nowy kod używa modelu obiektów programu Word, aby dodać tekst wzorcowy do każdego zapisanego dokumentu. Domyślnie plik kodu ThisAddIn zawiera następujący wygenerowany kod:

- Częściowa definicja `ThisAddIn` klasy. Ta klasa zapewnia punkt wejścia dla kodu i zapewnia dostęp do modelu obiektów programu Word. Aby uzyskać więcej informacji, zobacz [Program VSTO Add-ins (Dodatki programu VSTO).](../vsto/programming-vsto-add-ins.md) Pozostała część klasy `ThisAddIn` jest zdefiniowana w ukrytym pliku kodu, który nie powinien być modyfikowany.

- Programy `ThisAddIn_Startup` obsługi zdarzeń i `ThisAddIn_Shutdown` . Te procedury obsługi zdarzeń są wywoływane, gdy program Word ładuje i zwalnia dodatek VSTO. Użyj tych programów obsługi zdarzeń, aby zainicjować dodatek VSTO podczas ładowania i wyczyścić zasoby używane przez dodatek VSTO, gdy jest zwalniany. Aby uzyskać więcej informacji, zobacz [Zdarzenia w projektach pakietu Office.](../vsto/events-in-office-projects.md)

### <a name="to-add-a-paragraph-of-text-to-the-saved-document"></a>Aby dodać akapit tekstu do zapisanego dokumentu

1. W pliku kodu ThisAddIn dodaj następujący kod do `ThisAddIn` klasy . Nowy kod definiuje program obsługi zdarzeń dla zdarzenia, które jest <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> wywoływane po zapisaniu dokumentu.

    Gdy użytkownik zapisuje dokument, program obsługi zdarzeń dodaje nowy tekst na początku dokumentu.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/FirstWordAddIn/ThisAddIn.vb" id="Snippet1":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs" id="Snippet1":::

   > [!NOTE]
   > Ten kod używa wartości indeksu 1, aby uzyskać dostęp do pierwszego akapitu w <xref:Microsoft.Office.Interop.Word._Document.Paragraphs%2A> kolekcji. Chociaż Visual Basic i Visual C# używają tablic opartych na 0, dolna granica tablicy większości kolekcji w modelu obiektów programu Word wynosi 1. Aby uzyskać więcej informacji, zobacz [Pisanie kodu w rozwiązaniach pakietu Office.](../vsto/writing-code-in-office-solutions.md)

2. Jeśli używasz języka C#, dodaj następujący wymagany kod do `ThisAddIn_Startup` procedury obsługi zdarzeń. Ten kod służy do łączenia programu `Application_DocumentBeforeSave` obsługi zdarzeń ze <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> zdarzeniem.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs" id="Snippet2":::

   Aby zmodyfikować dokument podczas jego zapisania, poprzednie przykłady kodu używają następujących obiektów:

- Pole `Application` klasy `ThisAddIn` . Pole `Application` zwraca <xref:Microsoft.Office.Interop.Word.Application> obiekt reprezentujący bieżące wystąpienie programu Word.

- Parametr `Doc` procedury obsługi zdarzeń <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> dla zdarzenia. Parametr `Doc` jest <xref:Microsoft.Office.Interop.Word.Document> obiektem, który reprezentuje zapisany dokument. Aby uzyskać więcej informacji, zobacz [Omówienie modelu obiektów programu Word](../vsto/word-object-model-overview.md).

## <a name="test-the-project"></a>Testowanie projektu

### <a name="to-test-the-project"></a>Aby przetestować projekt

1. Naciśnij **klawisz F5,** aby skompilować i uruchomić projekt.

     Podczas kompilowania projektu kod jest kompilowany w zestawie, który znajduje się w folderze wyjściowym kompilacji dla projektu. Visual Studio tworzy również zestaw wpisów rejestru, które umożliwiają programowi Word odnajdywanie i ładowanie dodatku VSTO, a także konfiguruje ustawienia zabezpieczeń na komputerze dewelopera, aby umożliwić uruchamianie dodatku VSTO. Aby uzyskać więcej informacji, zobacz [Build Office solutions (Tworzenie rozwiązań pakietu Office).](../vsto/building-office-solutions.md)

2. W programie Word zapisz aktywny dokument.

3. Sprawdź, czy do dokumentu został dodany następujący tekst.

     **Ten tekst został dodany przy użyciu kodu.**

4. Zamknij program Word.

## <a name="clean-up-the-project"></a>Czyszczenie projektu
 Po zakończeniu tworzenia projektu usuń zestaw dodatku VSTO, wpisy rejestru i ustawienia zabezpieczeń z komputera dewelopera. W przeciwnym razie dodatek VSTO będzie nadal uruchamiany przy każdym otwarciu programu Word na komputerze dewelopera.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Aby wyczyścić ukończony projekt na komputerze dewelopera

1. W Visual Studio menu Build  (Kompilacja) kliknij pozycję **Clean Solution (Wyczyść rozwiązanie).**

## <a name="next-steps"></a>Następne kroki
 Po utworzeniu podstawowego dodatku VSTO dla programu Word możesz dowiedzieć się więcej na temat tworzenia dodatków VSTO z tych tematów:

- Ogólne zadania programistyczne, które można wykonywać w dodatki VSTO: [Dodatki programu VSTO.](../vsto/programming-vsto-add-ins.md)

- Zadania programistyczne specyficzne dla dodatków VSTO programu Word: [rozwiązania programu Word.](../vsto/word-solutions.md)

- Korzystanie z modelu obiektów programu Word: [Omówienie modelu obiektów Word](../vsto/word-object-model-overview.md).

- Dostosowywanie interfejsu użytkownika programu Word, na przykład przez dodanie karty niestandardowej do wstążki lub utworzenie własnego niestandardowego okienka zadań: Dostosowywanie interfejsu [użytkownika pakietu Office.](../vsto/office-ui-customization.md)

- Kompilowanie i debugowanie dodatków narzędzi VSTO dla programu Word: [tworzenie rozwiązań pakietu Office.](../vsto/building-office-solutions.md)

- Wdrażanie dodatków VSTO dla programu Word: [wdrażanie rozwiązania pakietu Office.](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>Zobacz też
- [Omówienie tworzenia rozwiązań pakietu Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Rozwiązania programu Word](../vsto/word-solutions.md)
- [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md)
- [Omówienie modelu obiektów programu Word](../vsto/word-object-model-overview.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)
- [Wdrażanie rozwiązania pakietu Office](../vsto/deploying-an-office-solution.md)
- [Omówienie szablonów projektów pakietu Office](../vsto/office-project-templates-overview.md)
