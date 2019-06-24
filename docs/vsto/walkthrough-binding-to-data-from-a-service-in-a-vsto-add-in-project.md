---
title: Powiąż z danymi z usługi w projekcie dodatku narzędzi VSTO
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
ms.openlocfilehash: c6278e4e849d698097fe3760411a3121d977df07
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328855"
---
# <a name="walkthrough-bind-to-data-from-a-service-in-a-vsto-add-in-project"></a>Przewodnik: Powiąż z danymi z usług w projektach dodatku narzędzi VSTO
  Dane można powiązać kontrolki hosta w projektach dodatku narzędzi VSTO. W tym instruktażu pokazano, jak dodać kontrolki do dokumentu programu Microsoft Office Word, powiązać formanty danych pobranych z usługi zawartości MSDN i reagowania na zdarzenia w czasie wykonywania.

 **Dotyczy:** Informacje przedstawione w tym temacie dotyczą projektów na poziomie aplikacji dla programu Word 2010. Aby uzyskać więcej informacji, zobacz [Dostępne funkcje uporządkowane według aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).

 W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie <xref:Microsoft.Office.Tools.Word.RichTextContentControl> kontrolki do dokumentu w czasie wykonywania.

- Powiązanie <xref:Microsoft.Office.Tools.Word.RichTextContentControl> kontrolki z danymi z usługi sieci web.

- Odpowiadanie na <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> zdarzenia <xref:Microsoft.Office.Tools.Word.RichTextContentControl> kontroli.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-a-new-project"></a>Tworzenie nowego projektu
 Pierwszym krokiem jest utworzenie projektu dodatku narzędzi VSTO programu Word.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt dodatku narzędzi VSTO programu Word z nazwą **usługi zawartości MTPS**, przy użyciu języka Visual Basic lub C#.

     Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Zostanie otwarty program Visual Studio `ThisAddIn.vb` lub `ThisAddIn.cs` plik i dodaje projekt do **Eksploratora rozwiązań**.

## <a name="add-a-web-service"></a>Dodaj usługę sieci web
 W ramach tego przewodnika należy użyć usługi sieci web o nazwie MTPS usługi zawartości. Ta usługa sieci web zwraca informacje z określonego artykuł w witrynie MSDN w postaci ciągu XML lub zwykłego tekstu. Dalszej części przedstawiono sposób wyświetlania zwracanych informacji w formancie zawartości.

### <a name="to-add-the-mtps-content-service-to-the-project"></a>Aby dodać usługę zawartości MTPS do projektu

1. Na **danych** menu, kliknij przycisk **Dodaj nowe źródło danych**.

2. W **Kreatora konfiguracji źródła danych**, kliknij przycisk **usługi**, a następnie kliknij przycisk **dalej**.

3. W **adres** wpisz następujący adres URL:

     **http://services.msdn.microsoft.com/ContentServices/ContentService.asmx**

4. Kliknij przycisk **Przejdź**.

5. W **Namespace** wpisz **ContentService**i kliknij przycisk **OK**.

6. W **Kreatora dodawania odwołania** okno dialogowe, kliknij przycisk **Zakończ**.

## <a name="add-a-content-control-and-bind-to-data-at-runtime"></a>Dodaj kontrolkę zawartości i powiąż z danymi w czasie wykonywania
 W projektach dodatku narzędzi VSTO dla programów należy dodać i powiązywanie kontrolek w czasie wykonywania. W tym przewodniku należy skonfigurować formantu zawartości do pobierania danych z usługi sieci web, po kliknięciu wewnątrz formantu.

### <a name="to-add-a-content-control-and-bind-to-data"></a>Aby dodać kontrolkę zawartości i powiąż z danymi

1. W `ThisAddIn` klasy, Zadeklaruj zmienne w usłudze zawartości MTPS, formant zawartości i powiązanie danych.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#2](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#2)]

2. Dodaj następującą metodę do `ThisAddIn` klasy. Ta metoda tworzy kontrolkę zawartości na początku aktywnego dokumentu.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#4](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#4](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#4)]

3. Dodaj następującą metodę do `ThisAddIn` klasy. Ta metoda inicjuje obiektów potrzebnych do tworzenia i Wyślij żądanie do usługi sieci web.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#6](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#6)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#6](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#6)]

4. Utwórz procedurę obsługi zdarzeń do pobrania dokumentu biblioteki MSDN Library o zawartości kontrolki, gdy użytkownik kliknie wewnątrz zawartości kontrolować i powiązania danych do formantu zawartości.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#5](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#5](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#5)]

5. Wywołaj `AddRichTextControlAtRange` i `InitializeServiceObjects` metody z `ThisAddIn_Startup` metody. Dla programistów C# Dodaj program obsługi zdarzeń.

     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#3](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#3)]

## <a name="test-the-add-in"></a>Testowanie dodatku programu
 Po otwarciu programu Word, <xref:Microsoft.Office.Tools.Word.RichTextContentControl> formant jest widoczny. Tekst w zmiany kontroli po kliknięciu wewnątrz niego.

### <a name="to-test-the-vsto-add-in"></a>Aby przetestować dodatku narzędzi VSTO

1. Naciśnij klawisz **F5**.

2. Kliknij wewnątrz formantu zawartości.

     Informacje są pobierane z usługi zawartości MTPS i wyświetlany w formancie zawartości.

## <a name="see-also"></a>Zobacz także
- [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
