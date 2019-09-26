---
title: Powiąż z danymi z usługi w projekcie dodatku VSTO
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 74a43a0c601fa8a96c8737644bf5bd0261f59796
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254056"
---
# <a name="walkthrough-bind-to-data-from-a-service-in-a-vsto-add-in-project"></a>Przewodnik: Powiąż z danymi z usługi w projekcie dodatku VSTO
  Można powiązać dane z kontrolkami hosta w projektach dodatku VSTO. W tym instruktażu pokazano, jak dodać kontrolki do dokumentu programu Word Microsoft Office, powiązać kontrolki z danymi pobranymi z usługi zawartości MSDN i odpowiadać na zdarzenia w czasie wykonywania.

 **Dotyczy:** Informacje przedstawione w tym temacie dotyczą projektów na poziomie aplikacji dla programu Word 2010. Aby uzyskać więcej informacji, zobacz [Dostępne funkcje uporządkowane według aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).

 W instruktażu przedstawiono następujące zagadnienia:

- <xref:Microsoft.Office.Tools.Word.RichTextContentControl> Dodawanie kontrolki do dokumentu w czasie wykonywania.

- <xref:Microsoft.Office.Tools.Word.RichTextContentControl> Powiązywanie formantu z danymi z usługi sieci Web.

- Reagowanie na <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> zdarzenie <xref:Microsoft.Office.Tools.Word.RichTextContentControl> formantu.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-a-new-project"></a>Tworzenie nowego projektu
 Pierwszym krokiem jest utworzenie projektu dodatku VSTO dla programu Word.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt dodatku VSTO programu Word o nazwie **MTPS Content Service**, używając albo Visual Basic lub C#.

     Aby uzyskać więcej informacji, zobacz [jak: Utwórz projekty pakietu Office w programie](../vsto/how-to-create-office-projects-in-visual-studio.md)Visual Studio.

     Program Visual Studio otwiera `ThisAddIn.vb` plik `ThisAddIn.cs` lub i dodaje projekt do **Eksplorator rozwiązań**.

## <a name="add-a-web-service"></a>Dodaj usługę sieci Web
 W tym instruktażu należy użyć usługi sieci Web o nazwie MTPS Content Service. Ta usługa sieci Web zwraca informacje z określonego artykułu MSDN w postaci ciągu XML lub zwykłego tekstu. W późniejszym kroku pokazano, jak wyświetlić zwrócone informacje w kontrolce zawartości.

### <a name="to-add-the-mtps-content-service-to-the-project"></a>Aby dodać usługę zawartości MTPS do projektu

1. W menu **dane** kliknij polecenie **Dodaj nowe źródło danych**.

2. W **Kreatorze konfiguracji źródła danych**kliknij pozycję **Usługa**, a następnie kliknij przycisk **dalej**.

3. W polu **adres** wpisz następujący adres URL:

     **http:\//Services.MSDN.Microsoft.com/ContentServices/contentservice.asmx**

4. Kliknij przycisk **Przejdź**.

5. W polu **przestrzeń nazw** wpisz **contentservice**, a następnie kliknij przycisk **OK**.

6. W oknie dialogowym **Dodawanie odwołania kreatora** kliknij przycisk **Zakończ**.

## <a name="add-a-content-control-and-bind-to-data-at-run-time"></a>Dodaj kontrolkę zawartości i powiąż z danymi w czasie wykonywania
 W projektach dodatku VSTO Dodawanie i powiązywanie kontrolek w czasie wykonywania. W tym instruktażu Skonfiguruj kontrolkę zawartość, aby pobierać dane z usługi sieci Web, gdy użytkownik kliknie wewnątrz kontrolki.

### <a name="to-add-a-content-control-and-bind-to-data"></a>Aby dodać kontrolkę zawartości i powiązać ją z danymi

1. `ThisAddIn` W klasie Zadeklaruj zmienne dla usługi zawartości MTPS, kontrolki zawartości i powiązania danych.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#2](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#2)]

2. Dodaj następującą metodę do `ThisAddIn` klasy. Ta metoda tworzy kontrolkę zawartości na początku aktywnego dokumentu.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#4](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#4](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#4)]

3. Dodaj następującą metodę do `ThisAddIn` klasy. Ta metoda inicjuje obiekty, które są konieczne do utworzenia i wysłania żądania do usługi sieci Web.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#6](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#6)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#6](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#6)]

4. Utwórz procedurę obsługi zdarzeń, aby pobrać dokument biblioteki MSDN dotyczący formantów zawartości, gdy użytkownik kliknie wewnątrz kontrolki zawartości i powiąże dane z kontrolką zawartości.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#5](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#5](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#5)]

5. Wywoływanie metod `InitializeServiceObjects` `ThisAddIn_Startup` i przy użyciu metody. `AddRichTextControlAtRange` Dla C# programistów Dodaj program obsługi zdarzeń.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#3](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#3)]

## <a name="test-the-add-in"></a>Testowanie dodatku
 Po otwarciu programu Word <xref:Microsoft.Office.Tools.Word.RichTextContentControl> zostanie wyświetlony formant. Tekst w kontrolce zostanie zmieniony po kliknięciu jej wewnątrz.

### <a name="to-test-the-vsto-add-in"></a>Aby przetestować dodatek narzędzi VSTO

1. Naciśnij klawisz **F5**.

2. Kliknij wewnątrz kontrolki zawartość.

     Informacje są pobierane z usługi zawartości MTPS i wyświetlane wewnątrz kontrolki zawartości.

## <a name="see-also"></a>Zobacz także
- [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
