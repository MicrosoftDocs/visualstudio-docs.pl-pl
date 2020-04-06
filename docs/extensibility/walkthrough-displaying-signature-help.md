---
title: 'Przewodnik: Wyświetlanie Pomocy podpisu | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f85d7eb3959064468e7583ec0c8a927f3e139daf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697422"
---
# <a name="walkthrough-display-signature-help"></a>Instruktaż: Wyświetlanie pomocy podpisu
Pomoc podpisu (znana również jako *Informacje o parametrach)* wyświetla podpis metody w etykietce narzędzia, gdy użytkownik wpisuje znak początkowy listy parametrów (zazwyczaj nawias otwierający). Jako separator parametrów i parametrów (zazwyczaj przecinek) są wpisywane, etykietka narzędzia jest aktualizowana, aby wyświetlić następny parametr pogrubioną czcionką. Pomoc podpisu można zdefiniować w następujący sposób: w kontekście usługi językowej zdefiniować własne rozszerzenie nazwy pliku i typ zawartości oraz wyświetlić Pomoc podpisu tylko dla tego typu lub wyświetlić Pomoc podpisu dla istniejącego typu zawartości (na przykład "tekst"). W tym przewodniku pokazano, jak wyświetlić Pomoc podpisu dla typu zawartości "tekst".

 Pomoc podpisu jest zazwyczaj wyzwalana przez wpisanie określonego znaku, na przykład "(" (nawias otwierający) i odrzucana przez wpisanie innego znaku, na przykład ")" (nawias zamykający). Funkcje IntelliSense, które są wyzwalane przez wpisanie znaku można zaimplementować <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> za pomocą programu obsługi poleceń dla nacięć klawiszy (interfejs) i dostawcy obsługi, który implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfejs. Aby utworzyć źródło Pomocy podpisu, które jest listą podpisów <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> uczestniczących w Pomocy podpisu, należy zaimplementować interfejs i dostawcę źródłowego, który uruchamia <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> interfejs. Dostawcy są częściami składowymi managed extensibility Framework (MEF) i są odpowiedzialni za eksportowanie klas źródłowych <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>i kontrolerów oraz importowanie usług <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>i brokerów, na przykład , który umożliwia nawigację w buforze tekstowym, oraz za wyzwalanie sesji Pomocy podpisu.

 W tym przewodniku pokazano, jak skonfigurować Pomoc podpisu dla zakodowany zestaw identyfikatorów. W pełnych implementacjach język jest odpowiedzialny za dostarczanie tej zawartości.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-mef-project"></a>Tworzenie projektu MEF

#### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF

1. Utwórz projekt VSIX języka C#. (W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C# / Extensibility**, a następnie **VSIX Project**.) Nazwij `SignatureHelpTest`rozwiązanie .

2. Dodaj szablon elementu klasyfikatora edytora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Usuń istniejące pliki klas.

4. Dodaj następujące odwołania do projektu i upewnij się, że `false` **CopyLocal** jest ustawiona na:

     Edytor Microsoft.VisualStudio.Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft.VisualStudio.Shell.14.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-signature-help-signatures-and-parameters"></a>Implementowanie podpisów i parametrów Pomocy podpisu
 Źródło Pomocy podpisu jest oparte <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>na podpisach implementuujnych , z których każdy zawiera parametry implementujące <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>. W pełnej implementacji te informacje można uzyskać z dokumentacji języka, ale w tym przykładzie podpisy są zakodowane na czas.

#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Aby zaimplementować podpisy i parametry Pomocy podpisu

1. Dodaj plik klasy i `SignatureHelpSource`nadaj jego nazwę .

2. Dodaj następujące importy.

     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]

3. Dodaj klasę `TestParameter` o nazwie, która implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.

     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]

4. Dodaj konstruktora, który ustawia wszystkie właściwości.

     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]

5. Dodaj właściwości pliku <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.

     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]

6. Dodaj klasę `TestSignature` o nazwie, która implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.

     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]

7. Dodaj kilka pól prywatnych.

     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]

8. Dodaj konstruktora, który ustawia pola <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> i subskrybuje zdarzenie.

     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]

9. Zadeklaruj `CurrentParameterChanged` zdarzenie. To zdarzenie jest wywoływane, gdy użytkownik wypełnia jeden z parametrów w podpisie.

     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]

10. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> właściwość `CurrentParameterChanged` tak, aby wywołuje zdarzenie po zmianie wartości właściwości.

     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]

11. Dodaj metodę, która `CurrentParameterChanged` wywołuje zdarzenie.

     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]

12. Dodaj metodę obliczającą bieżący parametr, porównując liczbę przecinków w <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> liczbie przecinków w podpisie.

     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]

13. Dodaj program obsługi <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzeń dla `ComputeCurrentParameter()` zdarzenia, które wywołuje metodę.

     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]

14. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> właściwość. Ta właściwość <xref:Microsoft.VisualStudio.Text.ITrackingSpan> zawiera, który odpowiada zakres tekstu w buforze, do którego stosuje się podpis.

     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]

15. Zaimplementuj inne parametry.

     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]

## <a name="implement-the-signature-help-source"></a>Implementowanie źródła Pomocy podpisu
 Źródło Pomocy podpisu to zestaw podpisów, dla których podajesz informacje.

#### <a name="to-implement-the-signature-help-source"></a>Aby zaimplementować źródło Pomocy podpisu

1. Dodaj klasę `TestSignatureHelpSource` o nazwie, która implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.

     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]

2. Dodaj odwołanie do buforu tekstu.

     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]

3. Dodaj konstruktora, który ustawia bufor tekstu i dostawcę źródła Pomocy podpisu.

     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]

4. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> metodę. W tym przykładzie podpisy są zakodowane na czas, ale w pełnej implementacji można uzyskać te informacje z dokumentacji języka.

     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]

5. Metoda `CreateSignature()` pomocnika jest dostępna tylko dla ilustracji.

     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]

6. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> metodę. W tym przykładzie istnieją tylko dwa podpisy, z których każdy ma dwa parametry. W związku z tym ta metoda nie jest wymagana. W pełniejszej implementacji, w której dostępnych jest więcej niż jedno źródło Pomocy podpisu, ta metoda jest używana do decydowania, czy źródło Pomocy podpisu o najwyższym priorytecie może dostarczyć pasujący podpis. Jeśli nie, metoda zwraca null i źródło o najwyższym priorytecie jest proszony o podanie dopasowania.

     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]

7. Zaimplementuj `Dispose()` metodę:

     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]

## <a name="implement-the-signature-help-source-provider"></a>Implementowanie dostawcy źródła Pomocy podpisu
 Dostawca źródła Pomocy podpisu jest odpowiedzialny za eksportowanie części składnika Managed Extensibility Framework (MEF) i tworzenie wystąpienia źródła Pomocy podpisu.

#### <a name="to-implement-the-signature-help-source-provider"></a>Aby zaimplementować dostawcę źródła Pomocy podpisu

1. Dodaj klasę `TestSignatureHelpSourceProvider` o nazwie, która implementuje <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> i wyeksportuj <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>ją z , a "tekst" i Before ="default".

     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]

2. <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> Zaimplementuj `TestSignatureHelpSource`przez wystąpienie pliku .

     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]

## <a name="implement-the-command-handler"></a>Implementowanie programu obsługi poleceń
 Pomoc podpisu jest zazwyczaj wyzwalana przez nawias otwierający "(" znak i odrzucana przez nawias zamykający ")". Można obsługiwać te naciśnięcia <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> klawiszy, uruchamiając tak, że wyzwala sesji Pomocy podpisu po otrzymaniu znaku nawiasu otwierającego poprzedzonego nazwą znanej metody i odrzuca sesji po otrzymaniu znaku nawiasu zamykającego.

#### <a name="to-implement-the-command-handler"></a>Aby zaimplementować program obsługi poleceń

1. Dodaj klasę `TestSignatureHelpCommand` o nazwie, która implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.

     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]

2. Dodaj pola prywatne <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> dla karty (która umożliwia dodanie programu obsługi poleceń do łańcucha programów obsługi poleceń), widoku tekstu, brokera pomocy podpisu i sesji, a <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>i następnego <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.

     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]

3. Dodaj konstruktora, aby zainicjować te pola i dodać filtr poleceń do łańcucha filtrów poleceń.

     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]

4. Zaimplementuj <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodę wyzwalania sesji Pomocy podpisu, gdy filtr polecenia odbiera znak otwierający nawias "(" po jednej ze znanych nazw metod i aby odrzucić sesję, gdy otrzyma znak zamykający nawias ")", gdy sesja jest nadal aktywna. W każdym przypadku polecenie jest przekazywane dalej.

     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]

5. Zaimplementuj <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodę, aby zawsze przesyłała dalej polecenie.

     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]

## <a name="implement-the-signature-help-command-provider"></a>Implementowanie dostawcy polecenia Pomoc podpisu
 Można podać polecenie Pomoc podpisu, <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> implementując do tworzenia wystąpienia programu obsługi poleceń podczas tworzenia widoku tekstu.

### <a name="to-implement-the-signature-help-command-provider"></a>Aby zaimplementować dostawcę polecenia Pomoc podpisu

1. Dodaj klasę `TestSignatureHelpController` o nazwie, która implementuje <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>i <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>eksportuje ją za <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> <xref:Microsoft.VisualStudio.Utilities.NameAttribute>pomocą programów , i .

     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]

2. Zaimportuj <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (używane do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> uzyskania <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> <xref:Microsoft.VisualStudio.Text.Editor.ITextView>obiektu), (używane do znajdowania <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> bieżącego wyrazu) i (aby wyzwolić sesję Pomocy podpisu).

     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]

3. Zaimplementuj <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metodę, tworząc wystąpienie pliku `TestSignatureCommandHandler`.

     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]

## <a name="build-and-test-the-code"></a>Tworzenie i testowanie kodu
 Aby przetestować ten kod, skompiluj rozwiązanie SignatureHelpTest i uruchom go w wystąpieniu eksperymentalnym.

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Aby skompilować i przetestować rozwiązanie SignatureHelpTest

1. Skompiluj rozwiązanie.

2. Po uruchomieniu tego projektu w debugerze zostanie uruchomione drugie wystąpienie programu Visual Studio.

3. Utwórz plik tekstowy i wpisz tekst zawierający słowo "dodaj" oraz nawias otwierający.

4. Po wpisaniu nawiasu otwierającego powinna zostać wyświetlona etykietka narzędzia, która `add()` wyświetla listę dwóch podpisów dla metody.

## <a name="see-also"></a>Zobacz też
- [Instruktaż: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
