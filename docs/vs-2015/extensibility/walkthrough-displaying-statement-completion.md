---
title: 'Przewodnik: wyświetlanie uzupełniania instrukcji | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 37
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: db4e63beb1e3d4ff53e547492ae9eae7ee8001e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202010"
---
# <a name="walkthrough-displaying-statement-completion"></a>Przewodnik: wyświetlanie uzupełniania instrukcji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zaimplementować uzupełnianie instrukcji opartych na języku przez zdefiniowanie identyfikatorów, dla których chcesz wprowadzić zakończenie, a następnie wyzwalanie sesji ukończenia. Można zdefiniować uzupełnianie instrukcji w kontekście usługi językowej, zdefiniować własne rozszerzenie nazwy pliku i typ zawartości, a następnie wyświetlić uzupełnianie dla tego typu lub można wyzwolić ukończenie dla istniejącego typu zawartości — na przykład "zwykły tekst". W tym instruktażu pokazano, jak wyzwolić uzupełnianie instrukcji dla typu zawartości "zwykły tekst", który jest typem zawartości plików tekstowych. Typ zawartości "text" jest elementem nadrzędnym wszystkich innych typów zawartości, w tym kodu i plików XML.  
  
 Uzupełnianie instrukcji jest zazwyczaj wyzwalane przez wpisanie niektórych znaków — na przykład przez wpisanie początku identyfikatora, takiego jak "Using". Zwykle jest odrzucany przez wciśnięcie klawisza spacji, karty lub klawisza ENTER, aby zatwierdzić zaznaczenie. Można zaimplementować funkcje IntelliSense, które są wyzwalane przez wpisanie znaku przy użyciu programu obsługi poleceń dla naciśnięć klawiszy ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu) i dostawcy obsługi, który implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfejs. Aby utworzyć źródło uzupełniania, czyli listę identyfikatorów, które uczestniczą w ukończeniu, zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> interfejs i dostawcę źródła uzupełniania ( <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> interfejs). Dostawcy są częścią składników Managed Extensibility Framework (MEF). Są oni zobowiązani do eksportowania klas źródłowych i kontrolerów oraz importowania usług i brokerów — na przykład, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> który umożliwia nawigowanie w buforze tekstu, i <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> , który wyzwala sesję ukończenia.  
  
 W tym instruktażu pokazano, jak zaimplementować uzupełnianie instrukcji dla zakodowanego zestawu identyfikatorów. W przypadku pełnych implementacji usługa językowa i Dokumentacja języka są odpowiedzialne za dostarczanie tej zawartości.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Tworzenie projektu MEF  
  
#### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF  
  
1. Utwórz projekt VSIX języka C#. (W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C#/rozszerzalność**, a następnie **Projekt VSIX**). Nadaj nazwę rozwiązanie `CompletionTest` .  
  
2. Dodaj szablon elementu klasyfikatora edytora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Usuń istniejące pliki klas.  
  
4. Dodaj następujące odwołania do projektu i upewnij się, że **CopyLocal** jest ustawiona na `false` :  
  
     Microsoft. VisualStudio. Editor  
  
     Microsoft. VisualStudio. Language. IntelliSense  
  
     Microsoft. VisualStudio. OLE. Interop  
  
     Microsoft. VisualStudio. Shell. 14.0  
  
     Microsoft. VisualStudio. Shell. unzmienny. 10.0  
  
     Microsoft. VisualStudio. TextManager. Interop  
  
## <a name="implementing-the-completion-source"></a>Implementowanie źródła zakończenia  
 Źródło uzupełniania jest odpowiedzialne za gromadzenie zestawu identyfikatorów i dodawanie zawartości do okna zakończenia, gdy użytkownik wpisze wyzwalacz uzupełniania, taki jak pierwsze litery identyfikatora. W tym przykładzie identyfikatory i ich opisy są trwale kodowane w <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metodzie. W największej rzeczywistości można użyć parsera języka, aby uzyskać tokeny umożliwiające wypełnienie listy uzupełniania.  
  
#### <a name="to-implement-the-completion-source"></a>Aby zaimplementować Źródło ukończenia  
  
1. Dodaj plik klasy i nadaj mu nazwę `TestCompletionSource` .  
  
2. Dodaj następujące Importy:  
  
     [!code-csharp[VSSDKCompletionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#1)]
     [!code-vb[VSSDKCompletionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#1)]  
  
3. Zmodyfikuj deklarację klasy dla `TestCompletionSource` tak, aby implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> :  
  
     [!code-csharp[VSSDKCompletionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#2)]
     [!code-vb[VSSDKCompletionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#2)]  
  
4. Dodaj prywatne pola dla dostawcy źródłowego, bufora tekstu i listę <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> obiektów (które odpowiadają identyfikatorom, które będą uczestniczyć w sesji ukończenia):  
  
     [!code-csharp[VSSDKCompletionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#3)]
     [!code-vb[VSSDKCompletionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#3)]  
  
5. Dodaj konstruktora, który ustawia dostawcę źródłowego i bufor. `TestCompletionSourceProvider`Klasa jest definiowana w dalszych krokach:  
  
     [!code-csharp[VSSDKCompletionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#4)]
     [!code-vb[VSSDKCompletionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#4)]  
  
6. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metodę przez dodanie zestawu uzupełniania zawierającego zakończenia, które chcesz podać w kontekście. Każdy zestaw uzupełniający zawiera zestaw <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> zaawansowanych elementów i odpowiada karcie zakończenia okna. (W projektach Visual Basic karty okna zakończenia mają nazwę **wspólne** i **wszystkie**). Metoda FindTokenSpanAtPosition jest definiowana w następnym kroku.  
  
     [!code-csharp[VSSDKCompletionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#5)]
     [!code-vb[VSSDKCompletionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#5)]  
  
7. Poniższa metoda służy do znajdowania bieżącego wyrazu z położenia kursora:  
  
     [!code-csharp[VSSDKCompletionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#6)]
     [!code-vb[VSSDKCompletionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#6)]  
  
8. Zaimplementuj `Dispose()` metodę:  
  
     [!code-csharp[VSSDKCompletionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#7)]
     [!code-vb[VSSDKCompletionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#7)]  
  
## <a name="implementing-the-completion-source-provider"></a>Implementowanie dostawcy źródła ukończenia  
 Dostawca źródła zakończenia jest częścią składnika MEF, która tworzy wystąpienie źródła zakończenia.  
  
#### <a name="to-implement-the-completion-source-provider"></a>Aby zaimplementować dostawcę źródła ukończenia  
  
1. Dodaj klasę o nazwie `TestCompletionSourceProvider` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> . Wyeksportuj tę klasę z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "zwykłym tekstem" i <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ukończeniem testu".  
  
     [!code-csharp[VSSDKCompletionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#8)]
     [!code-vb[VSSDKCompletionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#8)]  
  
2. Zaimportuj a <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , który jest używany do znajdowania bieżącego wyrazu w źródle uzupełniania.  
  
     [!code-csharp[VSSDKCompletionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#9)]
     [!code-vb[VSSDKCompletionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#9)]  
  
3. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> metodę, aby utworzyć wystąpienie źródła uzupełniania.  
  
     [!code-csharp[VSSDKCompletionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#10)]
     [!code-vb[VSSDKCompletionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#10)]  
  
## <a name="implementing-the-completion-command-handler-provider"></a>Implementowanie dostawcy obsługi poleceń uzupełniania  
 Dostawca obsługi poleceń uzupełniania pochodzi od klasy <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> , która nasłuchuje zdarzenia tworzenia widoku tekstu i konwertuje widok z, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> który umożliwia dodanie polecenia do łańcucha poleceń programu Visual Studio Shell — do <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . Ponieważ ta klasa jest MEF eksportu, można jej również użyć do zaimportowania usług, które są wymagane przez program obsługi poleceń.  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>Aby zaimplementować dostawcę obsługi poleceń uzupełniania  
  
1. Dodaj plik o nazwie `TestCompletionCommandHandler` .  
  
2. Dodaj te instrukcje using:  
  
     [!code-csharp[VSSDKCompletionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#11)]
     [!code-vb[VSSDKCompletionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#11)]  
  
3. Dodaj klasę o nazwie `TestCompletionHandlerProvider` implementującej <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> . Wyeksportuj tę klasę z <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "programem obsługi uzupełniania tokenu", <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> z "zwykłym tekstem" i <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> z <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable> .  
  
     [!code-csharp[VSSDKCompletionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#12)]
     [!code-vb[VSSDKCompletionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#12)]  
  
4. Zaimportuj <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> , która umożliwia konwersję od a do a, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> a i a, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> która umożliwia dostęp do standardowych usług Visual Studio.  
  
     [!code-csharp[VSSDKCompletionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#13)]
     [!code-vb[VSSDKCompletionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#13)]  
  
5. Zaimplementuj <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metodę, aby utworzyć wystąpienie programu obsługi poleceń.  
  
     [!code-csharp[VSSDKCompletionTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#14)]
     [!code-vb[VSSDKCompletionTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#14)]  
  
## <a name="implementing-the-completion-command-handler"></a>Implementacja programu obsługi poleceń uzupełniania  
 Ponieważ uzupełnianie instrukcji jest wyzwalane przez naciśnięcia klawiszy, należy zaimplementować <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs, aby odbierać i przetwarzać naciśnięcia klawiszy, które wyzwalają, zatwierdzają i odrzucają sesję ukończenia.  
  
#### <a name="to-implement-the-completion-command-handler"></a>Aby zaimplementować procedurę obsługi polecenia uzupełniania  
  
1. Dodaj klasę o nazwie `TestCompletionCommandHandler` implementującej <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> :  
  
    [!code-csharp[VSSDKCompletionTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#15)]
    [!code-vb[VSSDKCompletionTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#15)]  
  
2. Dodaj pola prywatne dla następnej procedury obsługi polecenia (do którego zostanie przekazane polecenie), widoku tekstu, dostawcy obsługi poleceń (który umożliwia dostęp do różnych usług) i sesji ukończenia:  
  
    [!code-csharp[VSSDKCompletionTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#16)]
    [!code-vb[VSSDKCompletionTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#16)]  
  
3. Dodaj konstruktora, który ustawia widok tekstu i pola dostawcy, i dodaje polecenie do łańcucha poleceń:  
  
    [!code-csharp[VSSDKCompletionTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#17)]
    [!code-vb[VSSDKCompletionTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#17)]  
  
4. Zaimplementuj <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodę, przekazując polecenie:  
  
    [!code-csharp[VSSDKCompletionTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#18)]
    [!code-vb[VSSDKCompletionTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#18)]  
  
5. Zaimplementuj <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodę. Gdy ta metoda odbiera naciśnięcie klawisza, musi wykonać jedną z następujących czynności:  
  
   - Zezwalaj na zapisywanie znaku w buforze, a następnie wyzwalanie lub filtrowanie uzupełniania. (W tym celu należy wydrukować znaki).  
  
   - Zatwierdź ukończenie, ale nie Zezwalaj na zapisywanie znaku w buforze. (Odstępu, Tab i ENTER zrób to, gdy zostanie wyświetlona sesja ukończenia).  
  
   - Zezwalaj na przekazywanie polecenia do kolejnej procedury obsługi. (Wszystkie inne polecenia).  
  
     Ponieważ ta metoda może wyświetlać interfejs użytkownika, wywołaj, <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> Aby upewnić się, że nie jest wywoływana w kontekście usługi Automation:  
  
     [!code-csharp[VSSDKCompletionTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#19)]
     [!code-vb[VSSDKCompletionTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#19)]  
  
6. Ten kod jest metodą prywatną, która wyzwala sesję ukończenia:  
  
    [!code-csharp[VSSDKCompletionTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#20)]
    [!code-vb[VSSDKCompletionTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#20)]  
  
7. Następny przykład to Metoda prywatna, która anuluje subskrypcję <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> zdarzenia:  
  
    [!code-csharp[VSSDKCompletionTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#21)]
    [!code-vb[VSSDKCompletionTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#21)]  
  
## <a name="building-and-testing-the-code"></a>Kompilowanie i testowanie kodu  
 Aby przetestować ten kod, skompiluj rozwiązanie CompletionTest i uruchom je w eksperymentalnym wystąpieniu.  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>Aby skompilować i przetestować rozwiązanie CompletionTest  
  
1. Skompiluj rozwiązanie.  
  
2. Po uruchomieniu tego projektu w debugerze tworzone jest drugie wystąpienie programu Visual Studio.  
  
3. Utwórz plik tekstowy i wpisz tekst zawierający wyraz "Add".  
  
4. Po wpisaniu pierwszego "a", a następnie "d" powinna zostać wyświetlona lista zawierająca "dodanie" i "adaptacja". Zauważ, że dodanie jest zaznaczone. Gdy wpiszesz kolejną "d", lista powinna zawierać tylko "dodanie", która jest teraz zaznaczona. Możesz zatwierdzić "dodanie", naciskając spację, kartę lub klawisz ENTER lub Odrzuć listę, wpisując ESC lub dowolny inny klucz.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
