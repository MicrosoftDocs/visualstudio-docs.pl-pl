---
title: 'Przewodnik: Wyświetlanie uzupełniania instrukcji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 37
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 097cb671e15b75edd7e61f7860cf3a0c03123c9b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733038"
---
# <a name="walkthrough-displaying-statement-completion"></a>Przewodnik: wyświetlanie uzupełniania instrukcji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uzupełnianie instrukcji opartych na języku można zaimplementować poprzez określenie identyfikatorów, dla których chcesz udostępnić uzupełniania i następnie wyzwalania sesja kończenia. Można zdefiniować uzupełnianie instrukcji w kontekście usługi językowej, zdefiniować własne rozszerzenia nazwy pliku i typu zawartości i następnie wyświetlić uzupełnianie po prostu tego typu lub mogą wyzwalać zakończenia dla istniejącego typu zawartości — na przykład "plaintext". W tym przewodniku pokazano, jak wyzwolić uzupełniania instrukcji dla typu zawartości "w postaci zwykłego tekstu", który jest typem zawartości pliki tekstowe. Typ zawartości "text" jest element nadrzędny elementu wszystkich innych typów zawartości, w tym kodu i pliki XML.  
  
 Uzupełnianie instrukcji jest zazwyczaj wyzwalany po wpisaniu niektórych znaków — na przykład, wpisując początku identyfikatora takiego jak "za pomocą". Jest ona zazwyczaj odrzucane, naciskając klawisz spacji, Tab lub Enter, aby potwierdzić wybór. Możesz zaimplementować funkcje IntelliSense, które są wyzwalane, wpisując znak za pomocą obsługi poleceń dla naciśnięcia klawiszy ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu) i dostawcy programu obsługi, który implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfejsu. Aby utworzyć źródło uzupełniania, w którym znajduje się lista identyfikatorów, które uczestniczą w uzupełniania, należy zaimplementować <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> interfejsu i dostawcy źródła ukończenia ( <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> interfejsu). Dostawcy są składnikami Managed Extensibility Framework (MEF). Odpowiadają za eksportowanie klas źródłowych i kontrolera i importowanie usługi i brokerzy — na przykład <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, co pozwala nawigacji w buforze tekstu i <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, która wyzwala sesja kończenia.  
  
 W tym przewodniku pokazano, jak zaimplementować uzupełniania instrukcji dla zestawu ustaloną identyfikatorów. W pełnej implementacji usługi językowej i dokumentacji języka są odpowiedzialne za świadczenie tej zawartości.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Tworzenie projektu MEF  
  
#### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF  
  
1.  Utwórz projekt VSIX języka C#. (W **nowy projekt** okno dialogowe, wybierz opcję **Visual C# / rozszerzalności**, następnie **projekt VSIX**.) Nazwij rozwiązanie `CompletionTest`.  
  
2.  Dodaj szablon elementu edytora klasyfikatora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Usuń istniejące pliki klasy.  
  
4.  Dodaj następujące odwołania do projektu i upewnij się, że **CopyLocal** ustawiono `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-the-completion-source"></a>Implementowanie źródłowego uzupełniania  
 Źródło zakończenia jest odpowiedzialny za zbieranie zestaw identyfikatorów i dodawanie zawartości do okna ukończenia, gdy użytkownik wpisuje wyzwalacza zakończenia, na przykład pierwszych liter identyfikatora. W tym przykładzie, identyfikatory oraz ich opisy są zakodowane w <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metody. W większości rzeczywistych zastosowaniach należy użyć analizatora swój język uzyskiwanie tokenów do wypełnienia listy uzupełniania.  
  
#### <a name="to-implement-the-completion-source"></a>Aby zaimplementować źródła uzupełniania  
  
1.  Dodaj plik klasy i nadaj mu nazwę `TestCompletionSource`.  
  
2.  Dodaj te importów:  
  
     [!code-csharp[VSSDKCompletionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#1)]
     [!code-vb[VSSDKCompletionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#1)]  
  
3.  Zmodyfikuj deklarację klasy dla `TestCompletionSource` tak, aby implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-csharp[VSSDKCompletionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#2)]
     [!code-vb[VSSDKCompletionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#2)]  
  
4.  Dodawanie pola prywatne dla dostawcy źródła, bufor tekstowy i listę <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> obiektów, (które odnoszą się do identyfikatorów, które będą uczestniczyć w sesja kończenia):  
  
     [!code-csharp[VSSDKCompletionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#3)]
     [!code-vb[VSSDKCompletionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#3)]  
  
5.  Dodaj Konstruktor, który ustawia dostawcy źródła i buforu. `TestCompletionSourceProvider` Klasa jest zdefiniowana w kolejnych krokach:  
  
     [!code-csharp[VSSDKCompletionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#4)]
     [!code-vb[VSSDKCompletionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#4)]  
  
6.  Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metody, dodając zestaw zakończenia, który zawiera uzupełnienia, chcesz udostępnić w kontekście. Każdy zestaw uzupełniania zawiera zbiór <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> uzupełniania, a odpowiada karta okna ukończenia. (W projektach języka Visual Basic o nazwie karty okna ukończenia **typowe** i **wszystkich**.) Metoda FindTokenSpanAtPosition jest zdefiniowana w następnym kroku.  
  
     [!code-csharp[VSSDKCompletionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#5)]
     [!code-vb[VSSDKCompletionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#5)]  
  
7.  Poniższa metoda jest używana do znajdowania bieżącego słowa z położenie kursora:  
  
     [!code-csharp[VSSDKCompletionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#6)]
     [!code-vb[VSSDKCompletionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#6)]  
  
8.  Implementowanie `Dispose()` metody:  
  
     [!code-csharp[VSSDKCompletionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#7)]
     [!code-vb[VSSDKCompletionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#7)]  
  
## <a name="implementing-the-completion-source-provider"></a>Implementowanie dostawcy źródła uzupełniania  
 Dostawca źródła zakończenia jest część składnik MEF, tworzącym źródła ukończenia.  
  
#### <a name="to-implement-the-completion-source-provider"></a>Do implementowania dostawcy źródła uzupełniania  
  
1.  Dodaj klasę o nazwie `TestCompletionSourceProvider` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Eksportowanie tej klasy przy użyciu <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "zwykłego tekstu" i <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "test zakończenia".  
  
     [!code-csharp[VSSDKCompletionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#8)]
     [!code-vb[VSSDKCompletionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#8)]  
  
2.  Importuj <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, która jest używana do znajdowania bieżącego słowa w źródle ukończenia.  
  
     [!code-csharp[VSSDKCompletionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#9)]
     [!code-vb[VSSDKCompletionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#9)]  
  
3.  Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> metodę, aby utworzyć wystąpienie źródła ukończenia.  
  
     [!code-csharp[VSSDKCompletionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#10)]
     [!code-vb[VSSDKCompletionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#10)]  
  
## <a name="implementing-the-completion-command-handler-provider"></a>Implementowanie dostawcy programu obsługi zakończenia polecenia  
 Dostawcy programu obsługi zakończenia polecenia jest tworzony na podstawie <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, który wykrywa zdarzenie tworzenia widoku tekstu i konwertuje widok z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>— które umożliwia dodanie polecenia do tworzenia łańcucha polecenia powłoki programu Visual Studio — aby <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Ponieważ ta klasa jest eksport MEF, możesz również służy do importowania usług, które są wymagane przez sam program obsługi poleceń.  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>Do implementowania dostawcy obsługi polecenia uzupełniania  
  
1.  Dodaj plik o nazwie `TestCompletionCommandHandler`.  
  
2.  Dodaj je za pomocą instrukcji:  
  
     [!code-csharp[VSSDKCompletionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#11)]
     [!code-vb[VSSDKCompletionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#11)]  
  
3.  Dodaj klasę o nazwie `TestCompletionHandlerProvider` implementującej <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Eksportowanie tej klasy przy użyciu <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "procedury obsługi zakończenia tokenu", <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "zwykłego tekstu", a <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> z <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.  
  
     [!code-csharp[VSSDKCompletionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#12)]
     [!code-vb[VSSDKCompletionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#12)]  
  
4.  Importuj <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, które umożliwia konwersję z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> do <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>i <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> umożliwiającej dostęp do usług Visual Studio w warstwie standardowa.  
  
     [!code-csharp[VSSDKCompletionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#13)]
     [!code-vb[VSSDKCompletionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#13)]  
  
5.  Implementowanie <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metodę, aby utworzyć wystąpienie program obsługi poleceń.  
  
     [!code-csharp[VSSDKCompletionTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#14)]
     [!code-vb[VSSDKCompletionTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#14)]  
  
## <a name="implementing-the-completion-command-handler"></a>Implementowanie polecenia procedury obsługi zakończenia  
 Ponieważ uzupełnianie instrukcji jest wyzwalany przez naciśnięć klawiszy, należy zaimplementować <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu odbierały i przetwarzały naciśnięć klawiszy, które wyzwalacza, Zatwierdź i Odrzuć sesja kończenia.  
  
#### <a name="to-implement-the-completion-command-handler"></a>Aby zaimplementować polecenia procedury obsługi zakończenia  
  
1. Dodaj klasę o nazwie `TestCompletionCommandHandler` implementującej <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
    [!code-csharp[VSSDKCompletionTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#15)]
    [!code-vb[VSSDKCompletionTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#15)]  
  
2. Dodaj pola prywatne, kolejna procedura obsługi polecenia (do którego należy przekazać polecenie), widoku tekstu, dostawcy obsługi polecenia (który umożliwia dostęp do różnych usług), a sesja kończenia:  
  
    [!code-csharp[VSSDKCompletionTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#16)]
    [!code-vb[VSSDKCompletionTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#16)]  
  
3. Dodaj Konstruktor, który ustawia widok tekstu i pola dostawcy i dodaje polecenia do tworzenia łańcucha polecenia:  
  
    [!code-csharp[VSSDKCompletionTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#17)]
    [!code-vb[VSSDKCompletionTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#17)]  
  
4. Implementowanie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody przez przekazanie polecenia wzdłuż:  
  
    [!code-csharp[VSSDKCompletionTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#18)]
    [!code-vb[VSSDKCompletionTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#18)]  
  
5. Implementowanie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody. Gdy ta metoda odbiera naciśnięcie klawisza, wykonaj jedną z tych czynności:  
  
   - Zezwalaj na znak do zapisania w buforze i następnie wyzwolić lub filtrowanie uzupełniania. (Znaki niedrukowane to zrobić.)  
  
   - Zatwierdź zakończenia, ale nie zezwalają na znak do zapisania w buforze. (Białe znaki, Tab lub Enter to wykonać po wyświetleniu sesja kończenia).  
  
   - Zezwalaj na polecenie, aby być przekazywane do następnej procedury obsługi. (Wszystkie inne polecenia.)  
  
     Ponieważ ta metoda może wyświetlić interfejs użytkownika, wywołaj <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> aby upewnić się, że nie jest wywoływana w kontekście usługi automation:  
  
     [!code-csharp[VSSDKCompletionTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#19)]
     [!code-vb[VSSDKCompletionTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#19)]  
  
6. Ten kod jest metody prywatnej, która wyzwala sesja kończenia:  
  
    [!code-csharp[VSSDKCompletionTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#20)]
    [!code-vb[VSSDKCompletionTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#20)]  
  
7. Następny przykład jest metodą prywatnej, która anuluje subskrypcje ze <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> zdarzeń:  
  
    [!code-csharp[VSSDKCompletionTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#21)]
    [!code-vb[VSSDKCompletionTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#21)]  
  
## <a name="building-and-testing-the-code"></a>Tworzenie i testowanie kodu  
 Aby przetestować ten kod, Kompiluj rozwiązanie CompletionTest, a następnie uruchomić go w doświadczalnym wystąpieniu.  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>Aby skompilować i przetestować rozwiązanie CompletionTest  
  
1.  Skompiluj rozwiązanie.  
  
2.  Po uruchomieniu tego projektu w debugerze drugiego wystąpienia programu Visual Studio jest uruchomiony.  
  
3.  Utwórz plik tekstowy i wpisz jakiś tekst, który zawiera wyraz "Dodaj".  
  
4.  Podczas wpisywania najpierw "a", a następnie "d" powinna być wyświetlana lista zawierająca "Dodawanie" i "dostosowanie". Należy zauważyć, że wybrano dodawania. Podczas wpisywania tekstu "d", lista może zawierać tylko "dodatkowe", który jest zaznaczony. Zatwierdź "dodatkowe", naciskając klawisz spacji, tabulatorów ani Enter lub odrzucić listę, wpisując Esc lub dowolny inny klawisz.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

