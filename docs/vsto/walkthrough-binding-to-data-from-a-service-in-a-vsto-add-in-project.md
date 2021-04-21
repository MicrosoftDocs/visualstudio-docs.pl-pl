---
title: Wiązanie z danymi z usługi w projekcie dodatku VSTO
description: Dowiedz się, jak dodawać kontrolki do dokumentu programu Microsoft Word, powiązać kontrolki z danymi pobranymi z usługi zawartości MSDN i reagować na zdarzenia w czasie uruchamiania.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b6993cb3eebc7641f4486bdc617ecb78e40aa05c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824531"
---
# <a name="walkthrough-bind-to-data-from-a-service-in-a-vsto-add-in-project"></a>Przewodnik: wiązanie z danymi z usługi w projekcie dodatku VSTO
  Dane można powiązać z kontrolkami hostów w projektach dodatków VSTO. W tym przewodniku pokazano, jak dodać kontrolki do dokumentu programu Microsoft Office Word, powiązać kontrolki z danymi pobranymi z usługi zawartości MSDN i reagować na zdarzenia w czasie uruchamiania.

 **Dotyczy:** Informacje zawarte w tym temacie dotyczą projektów na poziomie aplikacji dla programu Word 2010. Aby uzyskać więcej informacji, zobacz [Dostępne funkcje uporządkowane według aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).

 W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie <xref:Microsoft.Office.Tools.Word.RichTextContentControl> kontrolki do dokumentu w czasie uruchamiania.

- Powiązanie <xref:Microsoft.Office.Tools.Word.RichTextContentControl> kontrolki z danymi z usługi internetowej.

- Odpowiadanie na <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> zdarzenie <xref:Microsoft.Office.Tools.Word.RichTextContentControl> kontrolki.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-a-new-project"></a>Tworzenie nowego projektu
 Pierwszym krokiem jest utworzenie projektu dodatku Word VSTO.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt dodatku Word VSTO o nazwie **MTPS Content Service** przy użyciu Visual Basic lub C#.

     Aby uzyskać więcej informacji, [zobacz How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio plik lub i dodaje projekt do pliku `ThisAddIn.vb` `ThisAddIn.cs` **Eksplorator rozwiązań**.

## <a name="add-a-web-service"></a>Dodawanie usługi internetowej
 W tym przewodniku użyj usługi internetowej o nazwie usługa zawartości MTPS. Ta usługa internetowa zwraca informacje z określonego artykułu MSDN w postaci ciągu XML lub zwykłego tekstu. W kolejnym kroku pokazano, jak wyświetlić zwrócone informacje w kontrolce zawartości.

### <a name="to-add-the-mtps-content-service-to-the-project"></a>Aby dodać usługę zawartości MTPS do projektu

1. W menu **Dane** kliknij pozycję **Dodaj nowe źródło danych.**

2. W **Kreatorze konfiguracji źródła danych** kliknij pozycję **Usługa**, a następnie kliknij przycisk **Dalej.**

3. W polu **Adres** wpisz następujący adres URL:

   `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

4. Kliknij **pozycję Przejdź.**

5. W polu **Przestrzeń** nazw wpisz **ContentService** i kliknij przycisk **OK.**

6. W **oknie dialogowym Kreator dodawania** odwołania kliknij przycisk **Zakończ.**

## <a name="add-a-content-control-and-bind-to-data-at-run-time"></a>Dodawanie kontrolki zawartości i wiązanie z danymi w czasie uruchamiania
 W projektach dodatków VSTO można dodawać i powiązać kontrolki w czasie uruchamiania. W tym przewodniku skonfiguruj kontrolkę zawartości tak, aby pobierała dane z usługi internetowej, gdy użytkownik kliknie wewnątrz kontrolki.

### <a name="to-add-a-content-control-and-bind-to-data"></a>Aby dodać kontrolkę zawartości i powiązać z danymi

1. W klasie `ThisAddIn` zadeklaruj zmienne dla usługi zawartości MTPS, kontrolki zawartości i powiązania danych.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb" id="Snippet2":::

2. Dodaj następującą metodę do `ThisAddIn` klasy . Ta metoda tworzy kontrolkę zawartości na początku aktywnego dokumentu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb" id="Snippet4":::

3. Dodaj następującą metodę do `ThisAddIn` klasy . Ta metoda inicjuje obiekty potrzebne do utworzenia i wysłania żądania do usługi internetowej.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb" id="Snippet6":::

4. Utwórz program obsługi zdarzeń, aby pobrać dokument biblioteki MSDN na temat kontrolek zawartości, gdy użytkownik kliknie wewnątrz kontrolki zawartości i powiąż dane z kontrolką zawartości.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb" id="Snippet5":::

5. Wywołaj `AddRichTextControlAtRange` `InitializeServiceObjects` metody i z metody `ThisAddIn_Startup` . Dla programistów języka C# dodaj program obsługi zdarzeń.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb" id="Snippet3":::

## <a name="test-the-add-in"></a>Testowanie dodatku
 Po otwarciu programu Word zostanie <xref:Microsoft.Office.Tools.Word.RichTextContentControl> wyświetlona kontrolka. Tekst w kontrolce zmienia się po kliknięciu wewnątrz.

### <a name="to-test-the-vsto-add-in"></a>Aby przetestować dodatek VSTO

1. Naciśnij klawisz **F5**.

2. Kliknij wewnątrz kontrolki zawartości.

     Informacje są pobierane z usługi zawartości MTPS i wyświetlane wewnątrz kontrolki zawartości.

## <a name="see-also"></a>Zobacz też
- [Wiązanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
