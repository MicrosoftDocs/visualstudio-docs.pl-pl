---
title: 'Przewodnik: Wyświetlanie etykietek narzędzi QuickInfo | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: 47a14ca0692ad0338b56fd1d372307fb0e2ccc4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697436"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>Instruktaż: Wyświetlanie etykietek narzędzi QuickInfo
QuickInfo to funkcja IntelliSense, która wyświetla podpisy i opisy metod, gdy użytkownik przesuwa wskaźnik nad nazwą metody. Funkcje oparte na języku, takie jak QuickInfo, można zdefiniować identyfikatory, dla których chcesz podać opisy QuickInfo, a następnie utworzyć etykietkę narzędzia, w której mają być wyświetlane treści. QuickInfo można zdefiniować w kontekście usługi językowej lub zdefiniować własne rozszerzenie nazwy pliku i typ zawartości i wyświetlić QuickInfo tylko dla tego typu lub można wyświetlić QuickInfo dla istniejącego typu zawartości (na przykład "tekst"). W tym przewodniku pokazano, jak wyświetlić QuickInfo dla typu zawartości "tekst".

 QuickInfo przykład w tym instruktażu wyświetla etykietki narzędzi, gdy użytkownik przesuwa wskaźnik nad nazwą metody. Ten projekt wymaga zaimplementowania tych czterech interfejsów:

- interfejs źródłowy

- interfejs dostawcy źródła

- interfejs kontrolera

- interfejs dostawcy kontrolera

  Dostawcy źródła i kontrolera są częściami składowymi managed extensibility Framework (MEF) i są odpowiedzialni za eksportowanie klas źródłowych i kontrolerów oraz importowanie usług i brokerów, takich jak <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, który tworzy bufor tekstu etykietki narzędzia, i <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, który wyzwala sesję QuickInfo.

  W tym przykładzie źródło QuickInfo używa zakodowane listy nazw metod i opisów, ale w pełnych implementacjach usługi języka i dokumentacji języka są odpowiedzialne za dostarczanie tej zawartości.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie trzeba instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Tworzenie projektu MEF

### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF

1. Utwórz projekt VSIX języka C#. (W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C# / Extensibility**, a następnie **VSIX Project**.) Nazwij `QuickInfoTest`rozwiązanie .

2. Dodaj szablon elementu klasyfikatora edytora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Usuń istniejące pliki klas.

## <a name="implement-the-quickinfo-source"></a>Zaimplementowanie źródła QuickInfo
 Źródło QuickInfo jest odpowiedzialny za zbieranie zestaw identyfikatorów i ich opisy i dodawanie zawartości do buforu tekstu etykietki narzędzi, gdy jeden z identyfikatorów zostanie napotkany. W tym przykładzie identyfikatory i ich opisy są po prostu dodawane w konstruktorze źródłowym.

#### <a name="to-implement-the-quickinfo-source"></a>Aby zaimplementować źródło QuickInfo

1. Dodaj plik klasy i `TestQuickInfoSource`nadaj jego nazwę .

2. Dodaj odwołanie do witryny *Microsoft.VisualStudio.Language.IntelliSense*.

3. Dodaj następujące importy.

     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]

4. Deklaruj <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>klasę, która `TestQuickInfoSource`implementuje , i nazwij ją .

     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]

5. Dodaj pola dla dostawcy źródła QuickInfo, buforu tekstowego oraz zestawu nazw metod i podpisów metod. W tym przykładzie nazwy metod i podpisy `TestQuickInfoSource` są inicjowane w konstruktorze.

     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]

6. Dodaj konstruktora, który ustawia dostawcę źródła QuickInfo i bufor tekstowy i wypełnia zestaw nazw metod oraz podpisy i opisy metod.

     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]

7. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> metodę. W tym przykładzie metoda znajduje bieżący wyraz lub poprzedni wyraz, jeśli kursor znajduje się na końcu wiersza lub buforu tekstu. Jeśli wyraz jest jedną z nazw metod, opis tej nazwy metody jest dodawany do zawartości QuickInfo.

     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]

8. Należy również zaimplementować Dispose(), ponieważ <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implementuje: <xref:System.IDisposable>

     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]

## <a name="implement-a-quickinfo-source-provider"></a>Implementowanie dostawcy źródła QuickInfo
 Dostawca źródła QuickInfo służy przede wszystkim do eksportowania się jako część składnika MEF i wystąpienia źródła QuickInfo. Ponieważ jest to część składowa MEF, może importować inne części składowe MEF.

#### <a name="to-implement-a-quickinfo-source-provider"></a>Aby zaimplementować dostawcę źródła QuickInfo

1. Zadeklaruj dostawcę `TestQuickInfoSourceProvider` źródła <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>QuickInfo o <xref:Microsoft.VisualStudio.Utilities.NameAttribute> nazwie, który implementuje , <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> i wyeksportuj <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> go za pomocą "ToolTip QuickInfo Source", a before="default" i "text".

     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]

2. Zaimportuj <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>dwie usługi edytora i , jako właściwości . `TestQuickInfoSourceProvider`

     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]

3. Zaimplementuj, <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> aby zwrócić nowy `TestQuickInfoSource`plik .

     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]

## <a name="implement-a-quickinfo-controller"></a>Implementowanie kontrolera QuickInfo
 Kontrolery QuickInfo określają, kiedy jest wyświetlany quickinfo. W tym przykładzie QuickInfo pojawia się, gdy wskaźnik znajduje się nad wyrazem, który odpowiada jednej z nazw metod. Kontroler QuickInfo implementuje program obsługi zdarzeń aktywowania myszą, który wyzwala sesję QuickInfo.

### <a name="to-implement-a-quickinfo-controller"></a>Aby zaimplementować kontroler QuickInfo

1. Deklaruj <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>klasę, która `TestQuickInfoController`implementuje , i nazwij ją .

     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]

2. Dodaj pola prywatne dla widoku tekstu, bufory tekstu reprezentowane w widoku tekstowym, sesję QuickInfo i dostawcę kontrolera QuickInfo.

     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]

3. Dodaj konstruktora, który ustawia pola i dodaje program obsługi zdarzeń aktywowania wskaźnika myszy.

     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]

4. Dodaj program obsługi zdarzeń aktywowania wskaźnika myszy, który wyzwala sesję QuickInfo.

     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]

5. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> metodę, tak aby usuwała program obsługi zdarzeń aktywowania myszą, gdy kontroler jest odłączony od widoku tekstu.

     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]

6. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> metodę i <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> metodę jako puste metody w tym przykładzie.

     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]

## <a name="implementing-the-quickinfo-controller-provider"></a>Wdrażanie dostawcy kontrolera QuickInfo
 Dostawca kontrolera QuickInfo służy przede wszystkim do eksportowania się jako części składnika MEF i tworzenia wystąpienia kontrolera QuickInfo. Ponieważ jest to część składowa MEF, może importować inne części składowe MEF.

### <a name="to-implement-the-quickinfo-controller-provider"></a>Aby zaimplementować dostawcę kontrolera QuickInfo

1. `TestQuickInfoControllerProvider` Deklaruj klasę <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>o nazwie, <xref:Microsoft.VisualStudio.Utilities.NameAttribute> która implementuje , i wyeksportuj ją za pomocą "ToolTip QuickInfo Controller" i "text": <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>

     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]

2. Zaimportuj <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> jako właściwość.

     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]

3. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> metodę, tworząc wystąpienie kontrolera QuickInfo.

     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]

## <a name="build-and-test-the-code"></a>Twórz i testuj kod
 Aby przetestować ten kod, skompiluj rozwiązanie QuickInfoTest i uruchom go w wystąpieniu eksperymentalnym.

### <a name="to-build-and-test-the-quickinfotest-solution"></a>Aby utworzyć i przetestować rozwiązanie QuickInfoTest

1. Skompiluj rozwiązanie.

2. Po uruchomieniu tego projektu w debugerze zostanie uruchomione drugie wystąpienie programu Visual Studio.

3. Utwórz plik tekstowy i wpisz tekst zawierający słowa "add" i "subtract".

4. Przesuń wskaźnik nad jednym z wystąpień "dodaj". Podpis i opis `add` metody powinny być wyświetlane.

## <a name="see-also"></a>Zobacz też
- [Instruktaż: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
