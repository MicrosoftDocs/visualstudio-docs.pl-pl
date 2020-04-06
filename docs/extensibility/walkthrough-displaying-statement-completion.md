---
title: 'Przewodnik: Wyświetlanie uzupełniania instrukcji | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 1d2f5499511c9dc0bbb6711d0da630315384f8e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697414"
---
# <a name="walkthrough-display-statement-completion"></a>Instruktaż: Zakończenie instrukcji wyświetlania
Można zaimplementować uzupełnianie instrukcji oparte na języku, definiując identyfikatory, dla których chcesz zapewnić zakończenie, a następnie wyzwalając sesję zakończenia. Można zdefiniować uzupełnianie instrukcji w kontekście usługi języka, zdefiniować własne rozszerzenie nazwy pliku i typ zawartości, a następnie wyświetlić uzupełnianie tylko dla tego typu. Można też wyzwolić zakończenie dla istniejącego typu zawartości — na przykład "zwykły tekst". W tym instruktażu pokazano, jak wyzwolić uzupełnianie instrukcji dla typu zawartości "plaintext", który jest typem zawartości plików tekstowych. Typ zawartości "tekst" jest elementem nadrzędnym wszystkich innych typów zawartości, w tym plików kodu i XML.

 Uzupełnianie instrukcji jest zazwyczaj wyzwalane przez wpisanie określonych znaków — na przykład przez wpisanie początku identyfikatora, takiego jak "using". Zazwyczaj jest odrzucany przez naciśnięcie klawisza **Spacja**, **Tab**lub **Enter,** aby zatwierdzić zaznaczenie. Funkcje IntelliSense, które wyzwalają podczas wpisywania znaku przy użyciu programu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> obsługi poleceń dla nacięć klawiszy (interfejs) i dostawcy obsługi, który implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfejs. Aby utworzyć źródło ukończenia, które jest listą identyfikatorów, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> które uczestniczą w uzupełnieniu, należy zaimplementować interfejs i dostawcę źródła uzupełniania <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> (interfejs). Dostawcami są części składowe managed extensibility Framework (MEF). Są one odpowiedzialne za eksportowanie klas źródłowych i kontrolerów oraz importowanie usług i brokerów — na przykład <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, który umożliwia nawigację w buforze tekstu, oraz <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>za wyzwalanie sesji zakończenia.

 W tym przewodniku pokazano, jak zaimplementować uzupełnianie instrukcji dla zakodowany zestaw identyfikatorów. W pełnych implementacjach usługa językowa i dokumentacja językowa są odpowiedzialne za dostarczanie tej zawartości.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Tworzenie projektu MEF

#### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF

1. Utwórz projekt VSIX języka C#. (W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C# / Extensibility**, a następnie **VSIX Project**.) Nazwij `CompletionTest`rozwiązanie .

2. Dodaj szablon elementu klasyfikatora edytora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Usuń istniejące pliki klas.

4. Dodaj następujące odwołania do projektu i upewnij się, że `false` **CopyLocal** jest ustawiona na:

     Edytor Microsoft.VisualStudio.Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Powłoka Microsoft.VisualStudio.15.0

     Microsoft.VisualStudio.Shell.Niezmienne.10.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-the-completion-source"></a>Zaimplementowanie źródła uzupełniania
 Źródło uzupełniania jest odpowiedzialny za zbieranie zestawu identyfikatorów i dodawanie zawartości do okna uzupełniania, gdy użytkownik wpisuje wyzwalacz zakończenia, takich jak pierwsze litery identyfikatora. W tym przykładzie identyfikatory i ich opisy są <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> zakodowane na miejscu w metodzie. W większości rzeczywistych zastosowań, należy użyć analizatora języka, aby uzyskać tokeny do wypełnienia listy ukończenia.

### <a name="to-implement-the-completion-source"></a>Aby zaimplementować źródło ukończenia

1. Dodaj plik klasy i `TestCompletionSource`nadaj jego nazwę .

2. Dodaj te importy:

     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]

3. Zmodyfikuj deklarację klasy, aby `TestCompletionSource` wdrożyła: <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]

4. Dodaj pola prywatne dla dostawcy źródłowego, buforu <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> tekstowego i listy obiektów (które odpowiadają identyfikatorom, które będą uczestniczyć w sesji zakończenia):

     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]

5. Dodaj konstruktora, który ustawia dostawcę źródłowego i buforu. Klasa `TestCompletionSourceProvider` jest zdefiniowana w późniejszych krokach:

     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]

6. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metodę, dodając zestaw ukończenia, który zawiera uzupełnienia, które chcesz podać w kontekście. Każdy zestaw uzupełnień <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> zawiera zestaw uzupełnień i odpowiada karcie okna uzupełniania. (W projektach języka Visual Basic karty okna zakończenia mają nazwy **Wspólne** i **Wszystkie).** Metoda `FindTokenSpanAtPosition` jest zdefiniowana w następnym kroku.

     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]

7. Następująca metoda jest używana do znajdowania bieżącego wyrazu z pozycji kursora:

     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]

8. Zaimplementuj `Dispose()` metodę:

     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]

## <a name="implement-the-completion-source-provider"></a>Implementowanie dostawcy źródła uzupełniania
 Dostawca źródła uzupełniania jest częścią składnika MEF, która tworzenie wystąpienia źródła ukończenia.

### <a name="to-implement-the-completion-source-provider"></a>Aby zaimplementować dostawcę źródła ukończenia

1. Dodaj klasę `TestCompletionSourceProvider` o nazwie, która implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Wyeksportuj tę klasę <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> z <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "zwykłego tekstu" i "zakończenia testu".

     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]

2. Zaimportuj <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>program , który znajdzie bieżący wyraz w źródle uzupełniania.

     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]

3. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> metodę tworzenia wystąpienia źródła ukończenia.

     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]

## <a name="implement-the-completion-command-handler-provider"></a>Implementowanie dostawcy obsługi polecenia uzupełniania
 Dostawca obsługi poleceń uzupełniania <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>pochodzi od programu , który nasłuchuje zdarzenia tworzenia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>widoku tekstu i konwertuje widok z — który umożliwia <xref:Microsoft.VisualStudio.Text.Editor.ITextView>dodanie polecenia do łańcucha poleceń powłoki programu Visual Studio — na . Ponieważ ta klasa jest eksport MEF, można również użyć go do importowania usług, które są wymagane przez sam program obsługi poleceń.

#### <a name="to-implement-the-completion-command-handler-provider"></a>Aby zaimplementować dostawcę obsługi polecenia zakończenia

1. Dodawanie pliku `TestCompletionCommandHandler`o nazwie .

2. Dodaj te za pomocą dyrektyw:

     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]

3. Dodaj klasę `TestCompletionHandlerProvider` o nazwie, która implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Eksportuj tę <xref:Microsoft.VisualStudio.Utilities.NameAttribute> klasę z "programem <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> obsługi zakończenia tokenu", a "plaintext" i <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> . <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>

     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]

4. <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>Importuj , który <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> umożliwia <xref:Microsoft.VisualStudio.Text.Editor.ITextView>konwersję <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>z <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> a do , a i, który umożliwia dostęp do standardowych usług programu Visual Studio.

     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]

5. Zaimplementuj <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metodę tworzenia wystąpienia programu obsługi poleceń.

     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]

## <a name="implement-the-completion-command-handler"></a>Implementowanie programu obsługi polecenia uzupełniania
 Ponieważ uzupełnianie instrukcji jest wyzwalane przez naciśnięcia klawiszy, należy zaimplementować <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs, aby odbierać i przetwarzać naciśnięcia klawiszy, które wyzwalają, zatwierdzają i odrzucają sesję zakończenia.

#### <a name="to-implement-the-completion-command-handler"></a>Aby zaimplementować program obsługi polecenia zakończenia

1. Dodaj klasę `TestCompletionCommandHandler` o nazwie, która implementuje: <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>

    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]

2. Dodaj pola prywatne dla następnego programu obsługi poleceń (do którego przekazujesz polecenie), widok tekstowy, dostawcę obsługi poleceń (który umożliwia dostęp do różnych usług) i sesję zakończenia:

    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]

3. Dodaj konstruktor, który ustawia widok tekstu i pola dostawcy, i dodaje polecenie do łańcucha poleceń:

    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]

4. Zaimplementuj <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodę, przekazując polecenie wzdłuż:

    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]

5. Zaimplementuj <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodę. Gdy ta metoda odbiera naciśnięcie klawisza, musi wykonać jedną z następujących czynności:

   - Zezwalaj na zapisanie znaku w buforze, a następnie wyzwalanie lub uzupełnianie filtru. (Robią to znaki druku.

   - Zatwierdzić zakończenie, ale nie zezwalaj na znak, które mają być zapisywane w buforze. (Odstępy, **Tab**i **Enter** to zrobić, gdy wyświetlana jest sesja zakończenia).

   - Zezwalaj na przekazywanie polecenia do następnego programu obsługi. (Wszystkie inne polecenia).

     Ponieważ ta metoda może wyświetlać interfejsu użytkownika, wywołanie, <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> aby upewnić się, że nie jest wywoływana w kontekście automatyzacji:

     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]

6. Ten kod jest prywatną metodą, która wyzwala sesję zakończenia:

    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]

7. Następnym przykładem jest metoda prywatna, która wypisuje się z <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> wydarzenia:

    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]

## <a name="build-and-test-the-code"></a>Tworzenie i testowanie kodu
 Aby przetestować ten kod, skompiluj rozwiązanie CompletionTest i uruchom go w wystąpieniu eksperymentalnym.

#### <a name="to-build-and-test-the-completiontest-solution"></a>Aby skompilować i przetestować rozwiązanie CompletionTest

1. Skompiluj rozwiązanie.

2. Po uruchomieniu tego projektu w debugerze zostanie uruchomione drugie wystąpienie programu Visual Studio.

3. Utwórz plik tekstowy i wpisz tekst zawierający słowo "dodaj".

4. Podczas wpisywać najpierw "a", a następnie "d", powinna pojawić się lista zawierająca "dodawanie" i "adaptacja". Należy zauważyć, że dodatek jest zaznaczony. Po wpisaniu innego "d", lista powinna zawierać tylko "dodawanie", który jest teraz zaznaczony. Można zatwierdzić "dodawanie", naciskając **klawisz Spacja**, **Tab**lub **Enter,** lub odrzucić listę, wpisując klawisz Esc lub dowolny inny klawisz.

## <a name="see-also"></a>Zobacz też
- [Instruktaż: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
