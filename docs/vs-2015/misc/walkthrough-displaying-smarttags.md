---
title: 'Przewodnik: Wyświetlanie tagi inteligentne | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436512"
---
# <a name="walkthrough-displaying-smarttags"></a>Przewodnik: Wyświetlanie tagi inteligentne
Tagi inteligentne są przestarzałe na rzecz żarówki. Zobacz [instruktażu: Wyświetlanie sugestie z żarówką](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
 Tagi inteligentne są tagi w tekście, które rozwinąć w celu wyświetlenia działań. Na przykład w projekcie języka Visual Basic lub Visual C# czerwona linia będzie widoczna w wyrazu po zmianie nazwy identyfikatora, takie jak nazwa zmiennej. Gdy przesuniesz wskaźnik nad podkreślenie przycisku jest wyświetlany obok wskaźnika. Jeśli klikniesz przycisk, sugerowanej akcji jest wyświetlany, na przykład **IsRead Zmień nazwę, aby IsReady**. Jeśli klikniesz akcji, wszystkie odwołania do **IsRead** zostały zmienione w projekcie **IsReady**.  
  
 Mimo że tagi inteligentne są częścią implementacji funkcji IntelliSense w edytorze, można zaimplementować tagów inteligentnych przez podklasy <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>, a następnie wdrażanie <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> interfejsu i <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> interfejsu.  
  
> [!NOTE]
> W podobny sposób można zaimplementować innych rodzajów tagów.  
  
 Następujące instruktaż przedstawia sposób tworzenia tagu inteligentnego, pojawia się na bieżącego słowa, która ma dwa sugerowane akcje: **Konwertuj na wielkie litery** i **konwersji na małe litery**.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby skorzystać z tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Tworzenie projektu Framework (MEF) zarządzanych rozszerzeń  
  
#### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF  
  
1. Utwórz projekt Klasifikace edytora. Nazwij rozwiązanie `SmartTagTest`.  
  
2. Otwórz plik source.extension.vsixmanifest w edytorze manifestu VSIX.  
  
3. Upewnij się, że **zasoby** sekcja zawiera `Microsoft.VisualStudio.MefComponent` typu **źródła** ustawiono `A project in current solution`, i **projektu** jest ustawiona na SmartTagTest.dll.  
  
4. Zapisz i zamknij source.extension.vsixmanifest.  
  
5. Dodaj następujące odwołanie do projektu i ustaw **CopyLocal** do `false`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
6. Usuń istniejące pliki klasy.  
  
## <a name="implementing-a-tagger-for-smart-tags"></a>Implementowanie moduł Tagujący tagi inteligentne  
  
#### <a name="to-implement-a-tagger-for-smart-tags"></a>Aby zaimplementować moduł tagujący tagów inteligentnych  
  
1. Dodaj plik klasy i nadaj mu nazwę `TestSmartTag`.  
  
2. Dodaj następujące instrukcje importu:  
  
     [!code-csharp[VSSDKSmartTagTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#1)]
     [!code-vb[VSSDKSmartTagTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#1)]  
  
3. Dodaj klasę o nazwie `TestSmartTag` tej, która dziedziczy <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>.  
  
     [!code-csharp[VSSDKSmartTagTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#2)]
     [!code-vb[VSSDKSmartTagTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#2)]  
  
4. Dodaj Konstruktor dla tej klasy, która wywołuje konstruktora bazowego z <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> z <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>, co spowoduje niebieska linia były wyświetlane pod pierwszego znaku słowa. (Jeśli używasz <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>, czerwoną linią pojawią się w ostatnim znakiem słowa.)  
  
     [!code-csharp[VSSDKSmartTagTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#3)]
     [!code-vb[VSSDKSmartTagTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#3)]  
  
5. Dodaj klasę o nazwie `TestSmartTagger` tej, która dziedziczy <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> typu `TestSmartTag`i implementuje <xref:System.IDisposable>.  
  
     [!code-csharp[VSSDKSmartTagTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#4)]
     [!code-vb[VSSDKSmartTagTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#4)]  
  
6. Dodaj następujące pola prywatne do klasy moduł tagujący.  
  
     [!code-csharp[VSSDKSmartTagTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#5)]
     [!code-vb[VSSDKSmartTagTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#5)]  
  
7. Dodaj Konstruktor, który ustawia pola prywatne i subskrybuje <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> zdarzeń.  
  
     [!code-csharp[VSSDKSmartTagTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#6)]
     [!code-vb[VSSDKSmartTagTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#6)]  
  
8. Implementowanie <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> tak, aby tagu jest tworzona dla bieżącego słowa. (Ta metoda wywołuje również metody prywatnej `GetSmartTagActions` , zostało wyjaśnione w dalszej części.)  
  
     [!code-csharp[VSSDKSmartTagTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#7)]
     [!code-vb[VSSDKSmartTagTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#7)]  
  
9. Dodaj `GetSmartTagActions` metodę, aby skonfigurować akcje tagu inteligentnego. Akcje, samodzielnie są implementowane w kolejnych krokach.  
  
     [!code-csharp[VSSDKSmartTagTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#8)]
     [!code-vb[VSSDKSmartTagTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#8)]  
  
10. Zadeklaruj `SmartTagsChanged` zdarzeń.  
  
     [!code-csharp[VSSDKSmartTagTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#9)]
     [!code-vb[VSSDKSmartTagTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#9)]  
  
11. Implementowanie `OnLayoutChanged` programu obsługi zdarzeń w celu podniesienia `TagsChanged` zdarzenie, które powoduje <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> do wywołania.  
  
     [!code-csharp[VSSDKSmartTagTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#10)]
     [!code-vb[VSSDKSmartTagTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#10)]  
  
12. Implementowanie <xref:System.IDisposable.Dispose%2A> metodę, tak że anuluje subskrypcje ze <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> zdarzeń.  
  
     [!code-csharp[VSSDKSmartTagTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#11)]
     [!code-vb[VSSDKSmartTagTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#11)]  
  
## <a name="implementing-the-smart-tag-tagger-provider"></a>Implementowanie dostawcy moduł Tagujący tagów inteligentnych  
  
#### <a name="to-implement-the-smart-tag-tagger-provider"></a>Do implementowania dostawcy moduł tagujący tagów inteligentnych  
  
1. Dodaj klasę o nazwie `TestSmartTagTaggerProvider` tej, która dziedziczy <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>. Wyeksportuj go z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> z "text" <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> z wcześniej = "default" i <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> z <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>.  
  
     [!code-csharp[VSSDKSmartTagTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#12)]
     [!code-vb[VSSDKSmartTagTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#12)]  
  
2. Importuj <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> jako właściwość.  
  
     [!code-csharp[VSSDKSmartTagTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#13)]
     [!code-vb[VSSDKSmartTagTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#13)]  
  
3. Implementowanie <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metody.  
  
     [!code-csharp[VSSDKSmartTagTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#14)]
     [!code-vb[VSSDKSmartTagTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#14)]  
  
## <a name="implementing-smart-tag-actions"></a>Implementowanie akcji tagu inteligentnego  
  
#### <a name="to-implement-smart-tag-actions"></a>Aby zaimplementować tagi inteligentne akcje  
  
1. Utwórz dwie klasy o nazwie pierwszy `UpperCaseSmartTagAction` i druga o nazwie `LowerCaseSmartTagAction`. Zarówno klasy implementować <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction>.  
  
    [!code-csharp[VSSDKSmartTagTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#15)]
    [!code-vb[VSSDKSmartTagTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#15)]  
  
    [!code-csharp[VSSDKSmartTagTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#16)]
    [!code-vb[VSSDKSmartTagTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#16)]  
  
   Obie klasy są podobne, z tą różnicą, że jeden wywołuje <xref:System.String.ToUpper%2A> i inne wywołania <xref:System.String.ToLower%2A>. W poniższych krokach opisano tylko klasy akcji wielkie litery, ale musi implementować zarówno klasy. Wykonaj kroki wykonania akcji wielkie litery jako wzorzec do wykonywania akcji małe litery.  
  
2. Zadeklaruj zestaw pól prywatnych.  
  
    [!code-csharp[VSSDKSmartTagTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#17)]
    [!code-vb[VSSDKSmartTagTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#17)]  
  
3. Dodaj Konstruktor, który ustawia pola.  
  
    [!code-csharp[VSSDKSmartTagTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#18)]
    [!code-vb[VSSDKSmartTagTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#18)]  
  
4. Implementuje właściwości w następujący sposób.  
  
    [!code-csharp[VSSDKSmartTagTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#19)]
    [!code-vb[VSSDKSmartTagTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#19)]  
  
5. Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction.Invoke%2A> metody, zastępując tekst w zakresie równoważnik wielkie litery.  
  
    [!code-csharp[VSSDKSmartTagTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#20)]
    [!code-vb[VSSDKSmartTagTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#20)]  
  
## <a name="building-and-testing-the-code"></a>Tworzenie i testowanie kodu  
 Aby przetestować ten kod, Kompiluj rozwiązanie SmartTagTest, a następnie uruchomić go w doświadczalnym wystąpieniu.  
  
#### <a name="to-build-and-test-the-smarttagtest-solution"></a>Aby skompilować i przetestować rozwiązanie SmartTagTest  
  
1. Skompiluj rozwiązanie.  
  
2. Po uruchomieniu tego projektu w debugerze drugiego wystąpienia programu Visual Studio jest uruchomiony.  
  
3. Utwórz plik tekstowy i wpisz jakiś tekst.  
  
     Niebieska linia powinna być wyświetlana w obszarze pierwszą literę pierwszy wyraz tekstu.  
  
4. Przesuń wskaźnik myszy nad niebieska linia.  
  
     Przycisk powinien zostać wyświetlony obok wskaźnika.  
  
5. Po kliknięciu przycisku, powinny być wyświetlane dwie sugerowane akcje: **Konwertuj na wielkie litery** i **konwersji na małe litery**. Jeśli klikniesz pierwszą akcją, cały tekst w bieżącego słowa powinny być konwertowane na wielkie litery. Jeśli klikniesz drugiej akcji, cały tekst powinny być konwertowane na małe litery.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)