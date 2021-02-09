---
title: 'Przewodnik: wyświetlanie uzupełniania instrukcji | Microsoft Docs'
description: Dowiedz się, jak zaimplementować uzupełnianie instrukcji opartych na języku dla zawartości w postaci zwykłego tekstu za pomocą tego przewodnika.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: acangialosi
ms.author: anthc
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 95c797de1e68b275fa1a36ec8fa1f97f665cfd18
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873921"
---
# <a name="walkthrough-display-statement-completion"></a>Przewodnik: Wyświetlanie instrukcji wyświetlania
Można zaimplementować uzupełnianie instrukcji opartych na języku przez zdefiniowanie identyfikatorów, dla których chcesz wprowadzić zakończenie, a następnie wyzwalanie sesji ukończenia. Można zdefiniować uzupełnianie instrukcji w kontekście usługi językowej, zdefiniować własne rozszerzenie nazwy pliku i typ zawartości, a następnie wyświetlić uzupełnianie dla tego typu. Można też wyzwolić zakończenie dla istniejącego typu zawartości — na przykład "zwykły tekst". W tym instruktażu pokazano, jak wyzwolić uzupełnianie instrukcji dla typu zawartości "zwykły tekst", który jest typem zawartości plików tekstowych. Typ zawartości "text" jest elementem nadrzędnym wszystkich innych typów zawartości, w tym kodu i plików XML.

 Uzupełnianie instrukcji jest zazwyczaj wyzwalane przez wpisanie niektórych znaków — na przykład przez wpisanie początku identyfikatora, takiego jak "Using". Zwykle jest ona odrzucana przez wciśnięcie klawisza **spacji**, **karty** lub klawisza **Enter** , aby zatwierdzić zaznaczenie. Funkcje IntelliSense, które są wyzwalane podczas wpisywania znaku, można zaimplementować przy użyciu procedury obsługi poleceń dla naciśnięć klawiszy ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu) i dostawcy obsługi, który implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfejs. Aby utworzyć źródło uzupełniania, czyli listę identyfikatorów, które uczestniczą w ukończeniu, zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> interfejs i dostawcę źródła uzupełniania ( <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> interfejs). Dostawcy są częścią składników Managed Extensibility Framework (MEF). Są oni zobowiązani do eksportowania klas źródłowych i kontrolerów oraz importowania usług i brokerów — na przykład, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> który umożliwia nawigowanie w buforze tekstu oraz <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> , który wyzwala sesję ukończenia.

 W tym instruktażu pokazano, jak zaimplementować uzupełnianie instrukcji dla zakodowanego zestawu identyfikatorów. W przypadku pełnych implementacji usługa językowa i Dokumentacja języka są odpowiedzialne za dostarczanie tej zawartości.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dołączana jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Tworzenie projektu MEF

#### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF

1. Utwórz projekt VSIX języka C#. (W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C#/rozszerzalność**, a następnie **Projekt VSIX**). Nadaj nazwę rozwiązanie `CompletionTest` .

2. Dodaj szablon elementu klasyfikatora edytora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Usuń istniejące pliki klas.

4. Dodaj następujące odwołania do projektu i upewnij się, że **CopyLocal** jest ustawiona na `false` :

     Microsoft. VisualStudio. Editor

     Microsoft. VisualStudio. Language. IntelliSense

     Microsoft. VisualStudio. OLE. Interop

     Microsoft. VisualStudio. Shell. 15.0

     Microsoft. VisualStudio. Shell. unzmienny. 10.0

     Microsoft. VisualStudio. TextManager. Interop

## <a name="implement-the-completion-source"></a>Implementowanie źródła zakończenia
 Źródło uzupełniania jest odpowiedzialne za gromadzenie zestawu identyfikatorów i dodawanie zawartości do okna zakończenia, gdy użytkownik wpisze wyzwalacz uzupełniania, taki jak pierwsze litery identyfikatora. W tym przykładzie identyfikatory i ich opisy są trwale kodowane w <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metodzie. W największej rzeczywistości można użyć parsera języka, aby uzyskać tokeny umożliwiające wypełnienie listy uzupełniania.

### <a name="to-implement-the-completion-source"></a>Aby zaimplementować Źródło ukończenia

1. Dodaj plik klasy i nadaj mu nazwę `TestCompletionSource` .

2. Dodaj następujące Importy:

     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]

3. Zmodyfikuj deklarację klasy dla `TestCompletionSource` tak, aby implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> :

     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]

4. Dodaj prywatne pola dla dostawcy źródłowego, bufora tekstu i listę <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> obiektów (które odpowiadają identyfikatorom, które będą uczestniczyć w sesji ukończenia):

     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]

5. Dodaj konstruktora, który ustawia dostawcę źródłowego i bufor. `TestCompletionSourceProvider`Klasa jest definiowana w dalszych krokach:

     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]

6. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metodę przez dodanie zestawu uzupełniania zawierającego zakończenia, które chcesz podać w kontekście. Każdy zestaw uzupełniający zawiera zestaw <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> zaawansowanych elementów i odpowiada karcie zakończenia okna. (W projektach Visual Basic karty okna zakończenia mają nazwę **wspólne** i **wszystkie**). `FindTokenSpanAtPosition` Metoda jest definiowana w następnym kroku.

     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]

7. Poniższa metoda służy do znajdowania bieżącego wyrazu z położenia kursora:

     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]

8. Zaimplementuj `Dispose()` metodę:

     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]

## <a name="implement-the-completion-source-provider"></a>Implementowanie dostawcy źródła ukończenia
 Dostawca źródła zakończenia jest częścią składnika MEF, która tworzy wystąpienie źródła zakończenia.

### <a name="to-implement-the-completion-source-provider"></a>Aby zaimplementować dostawcę źródła ukończenia

1. Dodaj klasę o nazwie `TestCompletionSourceProvider` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> . Wyeksportuj tę klasę z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "zwykłym tekstem" i <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ukończeniem testu".

     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]

2. Zaimportuj a <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , która umożliwia znalezienie bieżącego wyrazu w źródle zakończenia.

     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]

3. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> metodę, aby utworzyć wystąpienie źródła uzupełniania.

     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]

## <a name="implement-the-completion-command-handler-provider"></a>Implementowanie dostawcy obsługi poleceń uzupełniania
 Dostawca obsługi poleceń uzupełniania pochodzi od klasy <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> , która nasłuchuje zdarzenia tworzenia widoku tekstu i konwertuje widok z, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> który umożliwia dodanie polecenia do łańcucha poleceń programu Visual Studio Shell — do <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . Ponieważ ta klasa jest MEF eksportu, można jej również użyć do zaimportowania usług, które są wymagane przez program obsługi poleceń.

#### <a name="to-implement-the-completion-command-handler-provider"></a>Aby zaimplementować dostawcę obsługi poleceń uzupełniania

1. Dodaj plik o nazwie `TestCompletionCommandHandler` .

2. Dodaj następujące dyrektywy:

     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]

3. Dodaj klasę o nazwie `TestCompletionHandlerProvider` implementującej <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> . Wyeksportuj tę klasę z <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "programem obsługi uzupełniania tokenu", <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> z "zwykłym tekstem" i <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> z <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable> .

     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]

4. Zaimportuj <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> , która umożliwia konwersję od a do a, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> a i a, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> która umożliwia dostęp do standardowych usług Visual Studio.

     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]

5. Zaimplementuj <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metodę, aby utworzyć wystąpienie programu obsługi poleceń.

     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]

## <a name="implement-the-completion-command-handler"></a>Implementuj procedurę obsługi poleceń uzupełniania
 Ponieważ uzupełnianie instrukcji jest wyzwalane przez naciśnięcia klawiszy, należy zaimplementować <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs, aby odbierać i przetwarzać naciśnięcia klawiszy, które wyzwalają, zatwierdzają i odrzucają sesję ukończenia.

#### <a name="to-implement-the-completion-command-handler"></a>Aby zaimplementować procedurę obsługi polecenia uzupełniania

1. Dodaj klasę o nazwie `TestCompletionCommandHandler` implementującej <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> :

    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]

2. Dodaj pola prywatne dla następnej procedury obsługi polecenia (do którego zostanie przekazane polecenie), widoku tekstu, dostawcy obsługi poleceń (który umożliwia dostęp do różnych usług) i sesji ukończenia:

    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]

3. Dodaj konstruktora, który ustawia widok tekstu i pola dostawcy, i dodaje polecenie do łańcucha poleceń:

    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]

4. Zaimplementuj <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodę, przekazując polecenie:

    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]

5. Zaimplementuj <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodę. Gdy ta metoda odbiera naciśnięcie klawisza, musi wykonać jedną z następujących czynności:

   - Zezwalaj na zapisywanie znaku w buforze, a następnie wyzwalanie lub filtrowanie uzupełniania. (W tym celu należy wydrukować znaki).

   - Zatwierdź ukończenie, ale nie Zezwalaj na zapisywanie znaku w buforze. (Odstępu, **Tab** i **Enter** zrób to, gdy zostanie wyświetlona sesja ukończenia).

   - Zezwalaj na przekazywanie polecenia do kolejnej procedury obsługi. (Wszystkie inne polecenia).

     Ponieważ ta metoda może wyświetlać interfejs użytkownika, wywołaj, <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> Aby upewnić się, że nie jest wywoływana w kontekście usługi Automation:

     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]

6. Ten kod jest metodą prywatną, która wyzwala sesję ukończenia:

    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]

7. Następny przykład to Metoda prywatna, która anuluje subskrypcję <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> zdarzenia:

    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]

## <a name="build-and-test-the-code"></a>Kompiluj i Testuj kod
 Aby przetestować ten kod, skompiluj rozwiązanie CompletionTest i uruchom je w eksperymentalnym wystąpieniu.

#### <a name="to-build-and-test-the-completiontest-solution"></a>Aby skompilować i przetestować rozwiązanie CompletionTest

1. Skompiluj rozwiązanie.

2. Po uruchomieniu tego projektu w debugerze uruchomione jest drugie wystąpienie programu Visual Studio.

3. Utwórz plik tekstowy i wpisz tekst zawierający wyraz "Add".

4. Po wpisaniu pierwszego "a", a następnie "d" powinna być wyświetlana lista zawierająca "dodanie" i "adaptacja". Zauważ, że dodanie jest zaznaczone. Gdy wpiszesz kolejną "d", lista powinna zawierać tylko "dodanie", która jest teraz zaznaczona. Możesz zatwierdzić "dodanie", naciskając **spację**, **kartę** lub klawisz **Enter** lub Odrzuć listę, wpisując ESC lub dowolny inny klucz.

## <a name="see-also"></a>Zobacz też
- [Przewodnik: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
