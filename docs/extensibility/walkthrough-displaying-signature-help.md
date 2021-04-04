---
title: 'Przewodnik: Wyświetlanie pomocy dotyczącej podpisu | Microsoft Docs'
description: Dowiedz się, jak wyświetlać pomoc dotyczącą podpisu dla typu zawartości tekstowej przy użyciu tego przewodnika. Pomoc dotycząca podpisu Wyświetla podpis metody w etykietce narzędzia.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d6ffa2a0e646c11cb56d08ef91e3d7a4b9af7572
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217505"
---
# <a name="walkthrough-display-signature-help"></a>Przewodnik: Wyświetlanie pomocy dotyczącej podpisu
Pomoc dotycząca podpisu (znana także jako *Informacje o parametrach*) wyświetla podpis metody w etykietce narzędzia, gdy użytkownik wpisze znak początkowy listy parametrów (zazwyczaj nawias otwierający). Jako parametr i separator parametrów (zwykle przecinki) są wpisywane, etykietka narzędzia jest aktualizowana, aby pokazać następny parametr pogrubioną czcionką. Możesz zdefiniować pomoc dotyczącą podpisu w następujący sposób: w kontekście usługi językowej Zdefiniuj własne rozszerzenie nazwy pliku i typ zawartości oraz Wyświetl pomoc dotyczącą podpisu tylko dla tego typu lub Wyświetl pomoc dotyczącą podpisu dla istniejącego typu zawartości (na przykład "tekst"). W tym instruktażu pokazano, jak wyświetlić pomoc dotyczącą podpisu dla typu zawartości "text".

 Pomoc dotycząca podpisu jest zazwyczaj wyzwalana przez wpisanie określonego znaku, na przykład "(" otwierającego nawiasu klamrowego) i odrzucenie przez wpisanie innego znaku, na przykład ")" (nawias zamykający). Funkcje IntelliSense, które są wyzwalane przez wpisanie znaku, można zaimplementować za pomocą procedury obsługi poleceń dla naciśnięć klawiszy ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs) i dostawcy obsługi, który implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfejs. Aby utworzyć źródło pomocy dla podpisu, czyli listę podpisów, które uczestniczą w pomocy w sygnaturach, zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> interfejs i dostawcę źródłowego z uruchomionym <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> interfejsem. Dostawcy są częścią składników Managed Extensibility Framework (MEF) i są odpowiedzialni za eksportowanie klas źródłowych i kontrolerów oraz importowanie usług i brokerów, na przykład, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> który umożliwia nawigowanie w buforze tekstu oraz <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> , który wyzwala sesję pomocy podpisu.

 W tym instruktażu przedstawiono sposób konfigurowania pomocy podpisu dla zakodowanego zestawu identyfikatorów. W przypadku pełnych implementacji język jest odpowiedzialny za zapewnienie tej zawartości.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dołączana jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-mef-project"></a>Tworzenie projektu MEF

#### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF

1. Utwórz projekt VSIX języka C#. (W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C#/rozszerzalność**, a następnie **Projekt VSIX**). Nadaj nazwę rozwiązanie `SignatureHelpTest` .

2. Dodaj szablon elementu klasyfikatora edytora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Usuń istniejące pliki klas.

4. Dodaj następujące odwołania do projektu i upewnij się, że **CopyLocal** jest ustawiona na `false` :

     Microsoft. VisualStudio. Editor

     Microsoft. VisualStudio. Language. IntelliSense

     Microsoft. VisualStudio. OLE. Interop

     Microsoft. VisualStudio. Shell. 14.0

     Microsoft. VisualStudio. TextManager. Interop

## <a name="implement-signature-help-signatures-and-parameters"></a>Implementowanie sygnatur i parametrów pomocy dla sygnatur
 Źródło pomocy podpisu jest oparte na sygnaturach, które implementują <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> , z których każdy zawiera parametry, które implementują <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> . W pełnej implementacji te informacje są uzyskiwane z dokumentacji języka, ale w tym przykładzie podpisy są zakodowane na stałe.

#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Aby zaimplementować sygnatury i parametry pomocy podpisu

1. Dodaj plik klasy i nadaj mu nazwę `SignatureHelpSource` .

2. Dodaj następujące Importy.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet1":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet1":::

3. Dodaj klasę o nazwie `TestParameter` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet2":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet2":::

4. Dodaj konstruktora, który ustawia wszystkie właściwości.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet3":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet3":::

5. Dodaj właściwości <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet4":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet4":::

6. Dodaj klasę o nazwie `TestSignature` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet5":::

7. Dodaj niektóre pola prywatne.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet6":::

8. Dodaj konstruktora, który ustawia pola i subskrybuje <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzenie.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet7":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet7":::

9. Zadeklaruj `CurrentParameterChanged` zdarzenie. To zdarzenie jest zgłaszane, gdy użytkownik wypełni jeden z parametrów w podpisie.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet8":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet8":::

10. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> Właściwość, aby zgłaszać `CurrentParameterChanged` zdarzenie, gdy wartość właściwości zostanie zmieniona.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet9":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet9":::

11. Dodaj metodę, która wywołuje `CurrentParameterChanged` zdarzenie.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet10":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet10":::

12. Dodaj metodę, która oblicza bieżący parametr, porównując liczbę przecinków w liczbie przecinków w <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> podpisie.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet11":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet11":::

13. Dodaj program obsługi zdarzeń dla <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzenia, które wywołuje `ComputeCurrentParameter()` metodę.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet12":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet12":::

14. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> Właściwość. Ta właściwość zawiera obiekt <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , który odnosi się do zakresu tekstu w buforze, do którego ma zastosowanie podpis.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet13":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet13":::

15. Zaimplementuj inne parametry.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet14":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet14":::

## <a name="implement-the-signature-help-source"></a>Implementowanie źródła pomocy dla podpisu
 Źródło pomocy podpisu to zbiór sygnatur, dla których informacje są podane.

#### <a name="to-implement-the-signature-help-source"></a>Aby zaimplementować źródło pomocy dla podpisu

1. Dodaj klasę o nazwie `TestSignatureHelpSource` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet15":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet15":::

2. Dodaj odwołanie do buforu tekstu.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet16":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet16":::

3. Dodaj konstruktora, który ustawia bufor tekstu i dostawcę źródła pomocy podpisu.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet17":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet17":::

4. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> metodę. W tym przykładzie podpisy są zakodowane na stałe, ale w pełnej implementacji można uzyskać te informacje z dokumentacji języka.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet18":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet18":::

5. Metoda pomocnika `CreateSignature()` jest dostępna tylko dla ilustracji.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet19":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet19":::

6. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> metodę. W tym przykładzie istnieją tylko dwa podpisy, z których każdy ma dwa parametry. W związku z tym ta metoda nie jest wymagana. W ramach większej implementacji, w której jest dostępny więcej niż jedno źródło pomocy dla podpisu, ta metoda jest używana do decydowania, czy źródło pomocy podpisu o najwyższym priorytecie może dostarczyć pasujący podpis. Jeśli nie jest to możliwe, metoda zwraca wartość null, a źródło następnego-o najwyższym priorytecie jest proszony o podanie dopasowania.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet20":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet20":::

7. Zaimplementuj `Dispose()` metodę:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet21":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet21":::

## <a name="implement-the-signature-help-source-provider"></a>Implementowanie dostawcy źródła pomocy dla podpisu
 Dostawca źródła pomocy dla podpisu jest odpowiedzialny za Eksportowanie części składnika Managed Extensibility Framework (MEF) i utworzenie wystąpienia źródła pomocy dla podpisu.

#### <a name="to-implement-the-signature-help-source-provider"></a>Aby zaimplementować dostawcę źródła pomocy dla podpisu

1. Dodaj klasę o nazwie `TestSignatureHelpSourceProvider` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> i wyeksportuj ją z <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , a <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> z "text" i od a do <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> = "default".

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet22":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet22":::

2. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> , tworząc wystąpienie elementu `TestSignatureHelpSource` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet23":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet23":::

## <a name="implement-the-command-handler"></a>Zaimplementuj procedurę obsługi poleceń
 Pomoc dotycząca podpisu jest zazwyczaj wyzwalana przez otwierając nawias "(" znak i odrzucony przez nawias zamykający ")". Możesz obsłużyć te nacionięcia klawiszy, uruchamiając polecenie, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Aby wyzwalał sesję pomocy w sygnaturze, gdy odbierze znak otwierającego nawiasu poprzedzony znaną nazwą metody i odrzuca sesję, gdy odbierze znak nawiasu zamykającego.

#### <a name="to-implement-the-command-handler"></a>Aby zaimplementować procedurę obsługi poleceń

1. Dodaj klasę o nazwie `TestSignatureHelpCommand` implementującej <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet24":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet24":::

2. Dodaj pola prywatne dla <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> karty (umożliwiającej dodanie programu obsługi poleceń do łańcucha programów obsługi poleceń), widok tekstu, sygnatura pomocy dla brokera i sesji, a <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> i dalej <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet25":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet25":::

3. Dodaj konstruktora, aby zainicjować te pola i dodać filtr polecenia do łańcucha filtrów poleceń.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet26":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet26":::

4. Zaimplementuj <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodę, aby wyzwolić sesję pomocy dotyczącej podpisu, gdy filtr poleceń odbiera nawias otwierający "(" znak po jednej z znanych nazw metod i aby odrzucić sesję, gdy odbierze nawias zamykający ")", gdy sesja jest nadal aktywna. W każdym przypadku polecenie jest przesyłane dalej.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet27":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet27":::

5. Zaimplementuj <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodę, aby zawsze przekazywać polecenie.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet28":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet28":::

## <a name="implement-the-signature-help-command-provider"></a>Implementowanie dostawcy poleceń pomocy dotyczącej podpisu
 Możesz podać polecenie pomocy do podpisu, implementując <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> procedurę obsługi poleceń podczas tworzenia widoku tekstu.

### <a name="to-implement-the-signature-help-command-provider"></a>Aby zaimplementować dostawcę poleceń pomocy dla podpisu

1. Dodaj klasę o nazwie `TestSignatureHelpController` implementującą <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> i wyeksportuj ją z <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> i <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet29":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet29":::

2. Zaimportuj <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (używany do uzyskania <xref:Microsoft.VisualStudio.Text.Editor.ITextView> , pod względem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> obiektu), <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (używany do znalezienia bieżącego wyrazu) i <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (aby wyzwolić sesję pomocy dla podpisu).

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet30":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet30":::

3. Zaimplementuj <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metodę, tworząc wystąpienie elementu `TestSignatureCommandHandler` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet31":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet31":::

## <a name="build-and-test-the-code"></a>Kompiluj i Testuj kod
 Aby przetestować ten kod, skompiluj rozwiązanie SignatureHelpTest i uruchom je w eksperymentalnym wystąpieniu.

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Aby skompilować i przetestować rozwiązanie SignatureHelpTest

1. Skompiluj rozwiązanie.

2. Po uruchomieniu tego projektu w debugerze uruchomione jest drugie wystąpienie programu Visual Studio.

3. Utwórz plik tekstowy i wpisz tekst zawierający wyraz "Add" oraz nawias otwierający.

4. Po wpisaniu nawiasu otwierającego powinna zostać wyświetlona etykietka narzędzia, która wyświetla listę dwóch podpisów dla `add()` metody.

## <a name="see-also"></a>Zobacz też
- [Przewodnik: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
