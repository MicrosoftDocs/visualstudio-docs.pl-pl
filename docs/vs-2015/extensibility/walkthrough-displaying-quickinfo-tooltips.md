---
title: 'Przewodnik: wyświetlanie etykietek narzędzi sekcji szybkich informacji | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3b349f0293071dfa30677b7558ca93985d16d55e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64808173"
---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>Przewodnik: wyświetlanie etykietek narzędzi SzybkieInfo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sekcji szybkich informacji to funkcja IntelliSense, która wyświetla sygnatury i opisy metod, gdy użytkownik przesuwa wskaźnik myszy nad nazwą metody. W celu zaimplementowania funkcji opartych na języku, takich jak sekcji szybkich informacji, można zdefiniować identyfikatory, dla których mają zostać wprowadzone opisy sekcji szybkich informacji, a następnie utworzyć etykietkę narzędzia, w której ma zostać wyświetlona zawartość. Można zdefiniować sekcji szybkich informacji w kontekście usługi językowej lub zdefiniować własne rozszerzenie nazwy pliku i typ zawartości oraz wyświetlić sekcji szybkich informacji dla danego typu. można też wyświetlić sekcji szybkich informacji dla istniejącego typu zawartości (na przykład "tekst"). W tym instruktażu pokazano, jak wyświetlić sekcji szybkich informacji dla typu zawartości "text".  
  
 W przykładzie sekcji szybkich informacji w tym instruktażu są wyświetlane etykietki narzędzi, gdy użytkownik przesuwa wskaźnik myszy nad nazwą metody. Ten projekt wymaga zaimplementowania tych czterech interfejsów:  
  
- Interfejs źródłowy  
  
- Interfejs dostawcy źródła  
  
- interfejs kontrolera  
  
- Interfejs dostawcy kontrolera  
  
  Dostawcy źródła i kontrolera są Managed Extensibility Framework części składników i są odpowiedzialni za eksportowanie klas źródłowych i kontrolerów oraz importowanie usług i brokerów, takich jak <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> , które tworzą bufor tekstu etykietki narzędzi, i <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> , które wyzwalają sesję sekcji szybkich informacji.  
  
  W tym przykładzie źródło sekcji szybkich informacji używa ustalonej listy nazw metod i opisów, ale w pełnych implementacjach usługa językowa i Dokumentacja języka są odpowiedzialne za dostarczanie tej zawartości.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Tworzenie projektu MEF  
  
#### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF  
  
1. Utwórz projekt VSIX języka C#. (W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C#/rozszerzalność**, a następnie **Projekt VSIX**). Nadaj nazwę rozwiązanie `QuickInfoTest` .  
  
2. Dodaj szablon elementu klasyfikatora edytora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Usuń istniejące pliki klas.  
  
## <a name="implementing-the-quickinfo-source"></a>Implementowanie źródła sekcji szybkich informacji  
 Źródło sekcji szybkich informacji jest odpowiedzialne za gromadzenie zestawu identyfikatorów i ich opisów oraz dodawanie zawartości do bufora tekstu etykietki narzędzia po napotkaniu jednego z identyfikatorów. W tym przykładzie identyfikatory i ich opisy są właśnie dodawane do konstruktora źródłowego.  
  
#### <a name="to-implement-the-quickinfo-source"></a>Aby zaimplementować źródło sekcji szybkich informacji  
  
1. Dodaj plik klasy i nadaj mu nazwę `TestQuickInfoSource` .  
  
2. Dodaj odwołanie do Microsoft. VisualStudio. Language. IntelliSense.  
  
3. Dodaj następujące Importy.  
  
     [!code-csharp[VSSDKQuickInfoTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#1)]
     [!code-vb[VSSDKQuickInfoTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#1)]  
  
4. Zadeklaruj klasę, która implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> , i nadaj jej nazwę `TestQuickInfoSource` .  
  
     [!code-csharp[VSSDKQuickInfoTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#2)]
     [!code-vb[VSSDKQuickInfoTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#2)]  
  
5. Dodawanie pól dla dostawcy źródła sekcji szybkich informacji, buforu tekstu oraz zestawu nazw metod i sygnatur metod. W tym przykładzie nazwy metod i podpisy są inicjowane w `TestQuickInfoSource` konstruktorze.  
  
     [!code-csharp[VSSDKQuickInfoTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#3)]
     [!code-vb[VSSDKQuickInfoTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#3)]  
  
6. Dodaj konstruktora, który ustawia dostawcę źródła sekcji szybkich informacji i bufor tekstu, i wypełnia zestaw nazw metod oraz sygnatury metod i opisy.  
  
     [!code-csharp[VSSDKQuickInfoTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#4)]
     [!code-vb[VSSDKQuickInfoTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#4)]  
  
7. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> metodę. W tym przykładzie metoda odnajduje bieżące słowo lub poprzednie słowo, jeśli kursor znajduje się na końcu wiersza lub buforu tekstu. Jeśli słowo jest jedną z nazw metod, opis tej nazwy metody jest dodawany do zawartości sekcji szybkich informacji.  
  
     [!code-csharp[VSSDKQuickInfoTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#5)]
     [!code-vb[VSSDKQuickInfoTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#5)]  
  
8. Należy również zaimplementować metodę Dispose (), ponieważ <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implementuje <xref:System.IDisposable> :  
  
     [!code-csharp[VSSDKQuickInfoTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#6)]
     [!code-vb[VSSDKQuickInfoTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#6)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>Implementowanie dostawcy źródła sekcji szybkich informacji  
 Dostawca źródła sekcji szybkich informacji służy głównie do eksportowania samego siebie jako części składnika MEF i tworzenia wystąpienia źródła sekcji szybkich informacji. Ponieważ jest częścią składnika MEF, może importować inne części składnika MEF.  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>Aby zaimplementować dostawcę źródła sekcji szybkich informacji  
  
1. Zadeklaruj dostawcę źródła sekcji szybkich informacji o nazwie, `TestQuickInfoSourceProvider` który implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider> , i wyeksportuj go za pomocą elementu <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ToolTip sekcji szybkich informacji source", <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> typu sprzed = "default" i typu <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text".  
  
     [!code-csharp[VSSDKQuickInfoTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#7)]
     [!code-vb[VSSDKQuickInfoTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#7)]  
  
2. Zaimportuj dwie usługi edytorów <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> i <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> , jako właściwości `TestQuickInfoSourceProvider` .  
  
     [!code-csharp[VSSDKQuickInfoTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#8)]
     [!code-vb[VSSDKQuickInfoTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#8)]  
  
3. Wdrożenie <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> w celu zwrócenia nowego elementu `TestQuickInfoSource` .  
  
     [!code-csharp[VSSDKQuickInfoTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#9)]
     [!code-vb[VSSDKQuickInfoTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#9)]  
  
## <a name="implementing-a-quickinfo-controller"></a>Implementowanie kontrolera sekcji szybkich informacji  
 Kontrolery sekcji szybkich informacji określają, kiedy mają być wyświetlane sekcji szybkich informacji. W tym przykładzie sekcji szybkich informacji jest wyświetlany, gdy wskaźnik znajduje się nad słowem, które odnosi się do jednej z nazw metod. Kontroler sekcji szybkich informacji implementuje procedurę obsługi zdarzeń przesuwania myszy, która wyzwala sesję sekcji szybkich informacji.  
  
#### <a name="to-implement-a-quickinfo-controller"></a>Aby zaimplementować kontroler sekcji szybkich informacji  
  
1. Zadeklaruj klasę, która implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> , i nadaj jej nazwę `TestQuickInfoController` .  
  
     [!code-csharp[VSSDKQuickInfoTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#10)]
     [!code-vb[VSSDKQuickInfoTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#10)]  
  
2. Dodaj pola prywatne dla widoku tekstu, bufory tekstu reprezentowane w widoku tekstu, sesji sekcji szybkich informacji i dostawcy kontrolera sekcji szybkich informacji.  
  
     [!code-csharp[VSSDKQuickInfoTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#11)]
     [!code-vb[VSSDKQuickInfoTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#11)]  
  
3. Dodaj konstruktora, który ustawia pola i dodaje procedurę obsługi zdarzeń przesuwania myszy.  
  
     [!code-csharp[VSSDKQuickInfoTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#12)]
     [!code-vb[VSSDKQuickInfoTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#12)]  
  
4. Dodaj program obsługi zdarzeń przesuwania myszy, który wyzwala sesję sekcji szybkich informacji.  
  
     [!code-csharp[VSSDKQuickInfoTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#13)]
     [!code-vb[VSSDKQuickInfoTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#13)]  
  
5. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> metodę, aby usunąć program obsługi zdarzeń przesuwania myszy, gdy kontroler zostanie odłączony od widoku tekstu.  
  
     [!code-csharp[VSSDKQuickInfoTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#14)]
     [!code-vb[VSSDKQuickInfoTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#14)]  
  
6. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> metodę i <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> metodę jako puste metody dla tego przykładu.  
  
     [!code-csharp[VSSDKQuickInfoTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#15)]
     [!code-vb[VSSDKQuickInfoTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#15)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>Implementowanie dostawcy kontrolera sekcji szybkich informacji  
 Dostawca kontrolera sekcji szybkich informacji służy głównie do eksportowania samego siebie jako części składnika MEF i tworzenia wystąpienia kontrolera sekcji szybkich informacji. Ponieważ jest częścią składnika MEF, może importować inne części składnika MEF.  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>Aby zaimplementować dostawcę kontrolera sekcji szybkich informacji  
  
1. Zadeklaruj klasę o nazwie `TestQuickInfoControllerProvider` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider> i wyeksportuj ją z <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "sekcji szybkich informacji etykietki narzędzia" i <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text":  
  
     [!code-csharp[VSSDKQuickInfoTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#16)]
     [!code-vb[VSSDKQuickInfoTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#16)]  
  
2. Zaimportuj <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> jako właściwość.  
  
     [!code-csharp[VSSDKQuickInfoTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#17)]
     [!code-vb[VSSDKQuickInfoTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#17)]  
  
3. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> metodę przez utworzenie wystąpienia kontrolera sekcji szybkich informacji.  
  
     [!code-csharp[VSSDKQuickInfoTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#18)]
     [!code-vb[VSSDKQuickInfoTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#18)]  
  
## <a name="building-and-testing-the-code"></a>Kompilowanie i testowanie kodu  
 Aby przetestować ten kod, skompiluj rozwiązanie QuickInfoTest i uruchom je w eksperymentalnym wystąpieniu.  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>Aby skompilować i przetestować rozwiązanie QuickInfoTest  
  
1. Skompiluj rozwiązanie.  
  
2. Po uruchomieniu tego projektu w debugerze tworzone jest drugie wystąpienie programu Visual Studio.  
  
3. Utwórz plik tekstowy i wpisz tekst zawierający słowa "Add" i "Odejmij".  
  
4. Przesuń wskaźnik na jedno z wystąpień elementu "Add". `add`Powinna zostać wyświetlona sygnatura i opis metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
