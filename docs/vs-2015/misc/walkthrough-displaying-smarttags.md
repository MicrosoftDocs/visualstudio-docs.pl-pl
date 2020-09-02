---
title: 'Przewodnik: wyświetlanie SmartTags | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - smart tags
ms.assetid: 10bb4f69-b259-41f0-b91a-69b04385d9a5
caps.latest.revision: 31
manager: jillfra
ms.openlocfilehash: 116f76324a2150413c0ae6d08bc99e114efcc50e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64805584"
---
# <a name="walkthrough-displaying-smarttags"></a>Przewodnik: wyświetlanie SmartTags
Tagi inteligentne są przestarzałe na rzecz żarówek. Zobacz [Przewodnik: wyświetlanie sugestii żarówki](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
 Tagi inteligentne to znaczniki tekstu, które rozwijają się w celu wyświetlenia zestawu akcji. Na przykład w projekcie w Visual Basic lub w języku Visual C# czerwona linia jest wyświetlana w obszarze wyrazu podczas zmiany nazwy identyfikatora, takiego jak nazwa zmiennej. Po przesunięciu wskaźnika nad podkreśleniem przycisk jest wyświetlany blisko wskaźnika. Jeśli klikniesz przycisk, zostanie wyświetlona Sugerowana akcja, na przykład **Zmień nazwę elementu isread na Isreaded**. Po kliknięciu akcji wszystkie odwołania do elementu **isread** w projekcie zostaną zmienione na wartość **isreaded**.  
  
 Chociaż Tagi inteligentne są częścią implementacji IntelliSense w edytorze, można zaimplementować Tagi inteligentne przez podklasy <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag> , a następnie implementując <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> interfejs i <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> interfejs.  
  
> [!NOTE]
> Inne rodzaje tagów można zaimplementować w podobny sposób.  
  
 W poniższym przewodniku pokazano, jak utworzyć inteligentny tag, który pojawia się w bieżącym wyrazie i ma dwie sugerowane akcje: **Konwertuj na wielkie litery** i **Konwertuj na małe litery**.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby wykonać czynności opisane w tym przewodniku, należy zainstalować Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Tworzenie projektu Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF  
  
1. Utwórz projekt klasyfikatora edytora. Nadaj nazwę rozwiązanie `SmartTagTest` .  
  
2. Otwórz plik source. Extension. vsixmanifest w edytorze manifestu VSIX.  
  
3. Upewnij się, że sekcja **składniki** zawiera `Microsoft.VisualStudio.MefComponent` Typ, **Źródło** jest ustawione na `A project in current solution` , a **projekt** jest ustawiony na SmartTagTest.dll.  
  
4. Zapisz i Zamknij źródło. Extension. vsixmanifest.  
  
5. Dodaj następujące odwołanie do projektu i ustaw **CopyLocal** na `false` :  
  
     Microsoft. VisualStudio. Language. IntelliSense  
  
6. Usuń istniejące pliki klas.  
  
## <a name="implementing-a-tagger-for-smart-tags"></a>Implementowanie moduł tagujący dla tagów inteligentnych  
  
#### <a name="to-implement-a-tagger-for-smart-tags"></a>Aby zaimplementować moduł tagujący dla tagów inteligentnych  
  
1. Dodaj plik klasy i nadaj mu nazwę `TestSmartTag` .  
  
2. Dodaj następujące Importy:  
  
     [!code-csharp[VSSDKSmartTagTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#1)]
     [!code-vb[VSSDKSmartTagTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#1)]  
  
3. Dodaj klasę o nazwie `TestSmartTag` , która dziedziczy z <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag> .  
  
     [!code-csharp[VSSDKSmartTagTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#2)]
     [!code-vb[VSSDKSmartTagTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#2)]  
  
4. Dodaj Konstruktor dla tej klasy, który wywołuje Konstruktor Base z <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> , co spowoduje, że niebieska linia zostanie wyświetlona pod pierwszym znakiem słowa. (Jeśli używasz <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> , czerwona linia zostanie wyświetlona w obszarze ostatniego znaku słowa).  
  
     [!code-csharp[VSSDKSmartTagTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#3)]
     [!code-vb[VSSDKSmartTagTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#3)]  
  
5. Dodaj klasę o nazwie `TestSmartTagger` , która dziedziczy z <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> typu `TestSmartTag` , i implementuje <xref:System.IDisposable> .  
  
     [!code-csharp[VSSDKSmartTagTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#4)]
     [!code-vb[VSSDKSmartTagTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#4)]  
  
6. Dodaj następujące prywatne pola do klasy moduł tagujący.  
  
     [!code-csharp[VSSDKSmartTagTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#5)]
     [!code-vb[VSSDKSmartTagTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#5)]  
  
7. Dodaj konstruktora, który ustawia pola prywatne i subskrybuje <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> zdarzenie.  
  
     [!code-csharp[VSSDKSmartTagTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#6)]
     [!code-vb[VSSDKSmartTagTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#6)]  
  
8. Zaimplementuj, <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Aby tag został utworzony dla bieżącego wyrazu. (Ta metoda wywołuje również metodę prywatną `GetSmartTagActions` , która została omówiona w dalszej części).  
  
     [!code-csharp[VSSDKSmartTagTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#7)]
     [!code-vb[VSSDKSmartTagTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#7)]  
  
9. Dodaj `GetSmartTagActions` metodę, aby skonfigurować akcje tagów inteligentnych. Same działania są implementowane w dalszych krokach.  
  
     [!code-csharp[VSSDKSmartTagTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#8)]
     [!code-vb[VSSDKSmartTagTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#8)]  
  
10. Zadeklaruj `SmartTagsChanged` zdarzenie.  
  
     [!code-csharp[VSSDKSmartTagTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#9)]
     [!code-vb[VSSDKSmartTagTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#9)]  
  
11. Zaimplementuj `OnLayoutChanged` procedurę obsługi zdarzeń, aby wywołać `TagsChanged` zdarzenie, które powoduje <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> wywołanie.  
  
     [!code-csharp[VSSDKSmartTagTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#10)]
     [!code-vb[VSSDKSmartTagTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#10)]  
  
12. Zaimplementuj <xref:System.IDisposable.Dispose%2A> metodę, aby anulować subskrypcję <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> zdarzenia.  
  
     [!code-csharp[VSSDKSmartTagTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#11)]
     [!code-vb[VSSDKSmartTagTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#11)]  
  
## <a name="implementing-the-smart-tag-tagger-provider"></a>Implementowanie dostawcy tagów inteligentnych moduł tagujący  
  
#### <a name="to-implement-the-smart-tag-tagger-provider"></a>Aby zaimplementować dostawcę tagów inteligentnych moduł tagujący  
  
1. Dodaj klasę o nazwie `TestSmartTagTaggerProvider` , która dziedziczy z <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> . Wyeksportuj go z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text", a <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> przed = "default" i <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> z <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag> .  
  
     [!code-csharp[VSSDKSmartTagTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#12)]
     [!code-vb[VSSDKSmartTagTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#12)]  
  
2. Zaimportuj <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> jako właściwość.  
  
     [!code-csharp[VSSDKSmartTagTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#13)]
     [!code-vb[VSSDKSmartTagTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#13)]  
  
3. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metodę.  
  
     [!code-csharp[VSSDKSmartTagTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#14)]
     [!code-vb[VSSDKSmartTagTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#14)]  
  
## <a name="implementing-smart-tag-actions"></a>Implementowanie akcji tagów inteligentnych  
  
#### <a name="to-implement-smart-tag-actions"></a>Aby zaimplementować Akcje tagów inteligentnych  
  
1. Utwórz dwie klasy, imię `UpperCaseSmartTagAction` i drugie o nazwie `LowerCaseSmartTagAction` . Obie klasy implementują <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction> .  
  
    [!code-csharp[VSSDKSmartTagTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#15)]
    [!code-vb[VSSDKSmartTagTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#15)]  
  
    [!code-csharp[VSSDKSmartTagTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#16)]
    [!code-vb[VSSDKSmartTagTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#16)]  
  
   Obie klasy są podobne, z wyjątkiem tego, że jedno wywołanie <xref:System.String.ToUpper%2A> i inne wywołania <xref:System.String.ToLower%2A> . Poniższe kroki dotyczą tylko klasy akcji wielkich liter, ale należy zaimplementować obie klasy. Wykonaj kroki w celu wdrożenia działania z wielką literą jako wzorca dla wdrożenia akcji małymi literami.  
  
2. Zadeklaruj zestaw pól prywatnych.  
  
    [!code-csharp[VSSDKSmartTagTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#17)]
    [!code-vb[VSSDKSmartTagTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#17)]  
  
3. Dodaj konstruktora, który ustawia pola.  
  
    [!code-csharp[VSSDKSmartTagTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#18)]
    [!code-vb[VSSDKSmartTagTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#18)]  
  
4. Zaimplementuj właściwości w następujący sposób.  
  
    [!code-csharp[VSSDKSmartTagTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#19)]
    [!code-vb[VSSDKSmartTagTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#19)]  
  
5. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction.Invoke%2A> metodę, zamieniając tekst w zakresie na jego wielką literę.  
  
    [!code-csharp[VSSDKSmartTagTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#20)]
    [!code-vb[VSSDKSmartTagTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#20)]  
  
## <a name="building-and-testing-the-code"></a>Kompilowanie i testowanie kodu  
 Aby przetestować ten kod, skompiluj rozwiązanie SmartTagTest i uruchom je w eksperymentalnym wystąpieniu.  
  
#### <a name="to-build-and-test-the-smarttagtest-solution"></a>Aby skompilować i przetestować rozwiązanie SmartTagTest  
  
1. Skompiluj rozwiązanie.  
  
2. Po uruchomieniu tego projektu w debugerze tworzone jest drugie wystąpienie programu Visual Studio.  
  
3. Utwórz plik tekstowy i wpisz tekst.  
  
     Niebieska linia powinna być wyświetlana poniżej pierwszej litery pierwszego wyrazu tekstu.  
  
4. Przesuń wskaźnik myszy nad niebieską linię.  
  
     Przycisk powinien być wyświetlany blisko wskaźnika.  
  
5. Po kliknięciu przycisku zostaną wyświetlone dwie sugerowane akcje: **Konwertuj na wielkie litery** i **Konwertuj na małe litery**. Po kliknięciu pierwszej akcji cały tekst w bieżącym wyrazie powinien zostać przekonwertowany na wielkie litery. Po kliknięciu drugiej akcji wszystkie teksty powinny być konwertowane na małe litery.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)