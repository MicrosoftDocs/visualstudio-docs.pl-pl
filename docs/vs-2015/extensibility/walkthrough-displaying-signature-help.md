---
title: 'Przewodnik: Wyświetlanie pomocy dotyczącej podpisu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 280b5b517089ad9e5b38cb00dc9b14c68253d1e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202048"
---
# <a name="walkthrough-displaying-signature-help"></a>Przewodnik: wyświetlanie pomocy dotyczącej sygnatur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomoc dotycząca podpisu (znana także jako *Informacje o parametrach*) wyświetla podpis metody w etykietce narzędzia, gdy użytkownik wpisze znak początkowy listy parametrów (zazwyczaj nawias otwierający). Jako parametr i separator parametrów (zwykle przecinki) są wpisywane, etykietka narzędzia jest aktualizowana, aby pokazać następny parametr pogrubioną czcionką. Można zdefiniować pomoc dotyczącą podpisu w kontekście usługi językowej lub można zdefiniować własne rozszerzenie nazwy pliku i typ zawartości oraz wyświetlić pomoc dotyczącą podpisu dla tego typu, lub można wyświetlić pomoc dotyczącą podpisu dla istniejącego typu zawartości (na przykład "tekst"). W tym instruktażu pokazano, jak wyświetlić pomoc dotyczącą podpisu dla typu zawartości "text".  
  
 Pomoc dotycząca podpisu jest zazwyczaj wyzwalana przez wpisanie określonego znaku, na przykład "(" otwierającego nawiasu klamrowego) i odrzucenie przez wpisanie innego znaku, na przykład ")" (nawias zamykający). Funkcje IntelliSense, które są wyzwalane przez wpisanie znaku, można zaimplementować za pomocą procedury obsługi poleceń dla naciśnięć klawiszy ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs) i dostawcy obsługi, który implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfejs. Aby utworzyć źródło pomocy dla podpisu, czyli listę podpisów, które uczestniczą w pomocy w sygnaturach, zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> interfejs i dostawcę źródłowego, który implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> interfejs. Dostawcy są częścią składników Managed Extensibility Framework (MEF) i są odpowiedzialni za eksportowanie klas źródłowych i kontrolerów oraz importowanie usług i brokerów, na przykład, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> który umożliwia nawigowanie w buforze tekstu oraz <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> , który wyzwala sesję pomocy podpisu.  
  
 W tym instruktażu przedstawiono sposób implementacji pomocy podpisu dla zakodowanego zestawu identyfikatorów. W przypadku pełnych implementacji język jest odpowiedzialny za zapewnienie tej zawartości.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Tworzenie projektu MEF  
  
#### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF  
  
1. Utwórz projekt VSIX języka C#. (W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C#/rozszerzalność**, a następnie **Projekt VSIX**). Nadaj nazwę rozwiązanie `SignatureHelpTest` .  
  
2. Dodaj szablon elementu klasyfikatora edytora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Usuń istniejące pliki klas.  
  
4. Dodaj następujące odwołania do projektu i upewnij się, że **CopyLocal** jest ustawiona na `false` :  
  
     Microsoft. VisualStudio. Editor  
  
     Microsoft. VisualStudio. Language. IntelliSense  
  
     Microsoft. VisualStudio. OLE. Interop  
  
     Microsoft. VisualStudio. Shell. 14.0  
  
     Microsoft. VisualStudio. TextManager. Interop  
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>Implementowanie sygnatur i parametrów pomocy dla sygnatur  
 Źródło pomocy podpisu jest oparte na sygnaturach, które implementują <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> , z których każdy zawiera parametry, które implementują <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> . W pełnej implementacji te informacje są uzyskiwane z dokumentacji języka, ale w tym przykładzie podpisy są zakodowane na stałe.  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Aby zaimplementować sygnatury i parametry pomocy podpisu  
  
1. Dodaj plik klasy i nadaj mu nazwę `SignatureHelpSource` .  
  
2. Dodaj następujące Importy.  
  
     [!code-csharp[VSSDKSignatureHelpTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#1)]
     [!code-vb[VSSDKSignatureHelpTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#1)]  
  
3. Dodaj klasę o nazwie `TestParameter` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#2)]
     [!code-vb[VSSDKSignatureHelpTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#2)]  
  
4. Dodaj konstruktora, który ustawia wszystkie właściwości.  
  
     [!code-csharp[VSSDKSignatureHelpTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#3)]
     [!code-vb[VSSDKSignatureHelpTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#3)]  
  
5. Dodaj właściwości <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#4)]
     [!code-vb[VSSDKSignatureHelpTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#4)]  
  
6. Dodaj klasę o nazwie `TestSignature` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#5)]
     [!code-vb[VSSDKSignatureHelpTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#5)]  
  
7. Dodaj niektóre pola prywatne.  
  
     [!code-csharp[VSSDKSignatureHelpTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#6)]
     [!code-vb[VSSDKSignatureHelpTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#6)]  
  
8. Dodaj konstruktora, który ustawia pola i subskrybuje <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzenie.  
  
     [!code-csharp[VSSDKSignatureHelpTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#7)]
     [!code-vb[VSSDKSignatureHelpTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#7)]  
  
9. Zadeklaruj `CurrentParameterChanged` zdarzenie. To zdarzenie jest zgłaszane, gdy użytkownik wypełni jeden z parametrów w podpisie.  
  
     [!code-csharp[VSSDKSignatureHelpTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#8)]
     [!code-vb[VSSDKSignatureHelpTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#8)]  
  
10. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> Właściwość, aby zgłaszać `CurrentParameterChanged` zdarzenie, gdy wartość właściwości zostanie zmieniona.  
  
     [!code-csharp[VSSDKSignatureHelpTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#9)]
     [!code-vb[VSSDKSignatureHelpTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#9)]  
  
11. Dodaj metodę, która wywołuje `CurrentParameterChanged` zdarzenie.  
  
     [!code-csharp[VSSDKSignatureHelpTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#10)]
     [!code-vb[VSSDKSignatureHelpTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#10)]  
  
12. Dodaj metodę, która oblicza bieżący parametr, porównując liczbę przecinków w liczbie przecinków w <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> podpisie.  
  
     [!code-csharp[VSSDKSignatureHelpTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#11)]
     [!code-vb[VSSDKSignatureHelpTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#11)]  
  
13. Dodaj program obsługi zdarzeń dla <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzenia, które wywołuje `ComputeCurrentParameter()` metodę.  
  
     [!code-csharp[VSSDKSignatureHelpTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#12)]
     [!code-vb[VSSDKSignatureHelpTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#12)]  
  
14. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> Właściwość. Ta właściwość zawiera obiekt <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , który odnosi się do zakresu tekstu w buforze, do którego ma zastosowanie podpis.  
  
     [!code-csharp[VSSDKSignatureHelpTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#13)]
     [!code-vb[VSSDKSignatureHelpTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#13)]  
  
15. Zaimplementuj inne parametry.  
  
     [!code-csharp[VSSDKSignatureHelpTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#14)]
     [!code-vb[VSSDKSignatureHelpTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#14)]  
  
## <a name="implementing-the-signature-help-source"></a>Implementowanie źródła pomocy dla podpisu  
 Źródło pomocy podpisu to zbiór sygnatur, dla których informacje są podane.  
  
#### <a name="to-implement-the-signature-help-source"></a>Aby zaimplementować źródło pomocy dla podpisu  
  
1. Dodaj klasę o nazwie `TestSignatureHelpSource` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#15)]
     [!code-vb[VSSDKSignatureHelpTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#15)]  
  
2. Dodaj odwołanie do buforu tekstu.  
  
     [!code-csharp[VSSDKSignatureHelpTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#16)]
     [!code-vb[VSSDKSignatureHelpTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#16)]  
  
3. Dodaj konstruktora, który ustawia bufor tekstu i dostawcę źródła pomocy podpisu.  
  
     [!code-csharp[VSSDKSignatureHelpTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#17)]
     [!code-vb[VSSDKSignatureHelpTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#17)]  
  
4. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> metodę. W tym przykładzie podpisy są zakodowane na stałe, ale w pełnej implementacji można uzyskać te informacje z dokumentacji języka.  
  
     [!code-csharp[VSSDKSignatureHelpTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#18)]
     [!code-vb[VSSDKSignatureHelpTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#18)]  
  
5. Metoda pomocnika `CreateSignature()` jest dostępna tylko dla ilustracji.  
  
     [!code-csharp[VSSDKSignatureHelpTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#19)]
     [!code-vb[VSSDKSignatureHelpTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#19)]  
  
6. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> metodę. W tym przykładzie istnieją tylko dwa podpisy, z których każdy ma dwa parametry. W związku z tym ta metoda nie jest wymagana. W ramach większej implementacji, w której jest dostępny więcej niż jedno źródło pomocy dla podpisu, ta metoda jest używana do decydowania, czy źródło pomocy podpisu o najwyższym priorytecie może dostarczyć pasujący podpis. Jeśli nie jest to możliwe, metoda zwraca wartość null, a źródło o najwyższym priorytecie jest proszony o podanie dopasowania.  
  
     [!code-csharp[VSSDKSignatureHelpTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#20)]
     [!code-vb[VSSDKSignatureHelpTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#20)]  
  
7. Zaimplementuj metodę Dispose ():  
  
     [!code-csharp[VSSDKSignatureHelpTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#21)]
     [!code-vb[VSSDKSignatureHelpTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#21)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>Implementowanie dostawcy źródła pomocy dla podpisu  
 Dostawca źródła pomocy dla podpisu jest odpowiedzialny za Eksportowanie części składnika Managed Extensibility Framework (MEF) i utworzenie wystąpienia źródła pomocy dla podpisu.  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>Aby zaimplementować dostawcę źródła pomocy dla podpisu  
  
1. Dodaj klasę o nazwie `TestSignatureHelpSourceProvider` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> i wyeksportuj ją z <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , a <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> z "text" i od a do <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> = "default".  
  
     [!code-csharp[VSSDKSignatureHelpTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#22)]
     [!code-vb[VSSDKSignatureHelpTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#22)]  
  
2. Zaimplementuj <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> , tworząc wystąpienie elementu `TestSignatureHelpSource` .  
  
     [!code-csharp[VSSDKSignatureHelpTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#23)]
     [!code-vb[VSSDKSignatureHelpTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#23)]  
  
## <a name="implementing-the-command-handler"></a>Implementowanie procedury obsługi poleceń  
 Pomoc dotycząca podpisu jest zazwyczaj wyzwalana przez znak (znak i odrzucony przez). Można obsłużyć te nacionięcia klawiszy przez implementację, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> tak aby wyzwalał sesję pomocy w przypadku odebrania (znak poprzedzony przez znaną nazwę metody i odrzucanie sesji po odebraniu znaku).  
  
#### <a name="to-implement-the-command-handler"></a>Aby zaimplementować procedurę obsługi poleceń  
  
1. Dodaj klasę o nazwie `TestSignatureHelpCommand` implementującej <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#24)]
     [!code-vb[VSSDKSignatureHelpTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#24)]  
  
2. Dodaj pola prywatne dla <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> karty (umożliwiającej dodanie programu obsługi poleceń do łańcucha programów obsługi poleceń), widok tekstu, sygnatura pomocy dla brokera i sesji, a <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> i dalej <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#25)]
     [!code-vb[VSSDKSignatureHelpTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#25)]  
  
3. Dodaj konstruktora, aby zainicjować te pola i dodać filtr polecenia do łańcucha filtrów poleceń.  
  
     [!code-csharp[VSSDKSignatureHelpTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#26)]
     [!code-vb[VSSDKSignatureHelpTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#26)]  
  
4. Zaimplementuj <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodę, aby wyzwolić sesję pomocy w sygnaturze, gdy filtr poleceń odbiera (znak po jednym z znanych nazw metod) i odrzucanie sesji po odebraniu znaku, gdy sesja jest nadal aktywna. W każdym przypadku polecenie jest przesyłane dalej.  
  
     [!code-csharp[VSSDKSignatureHelpTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#27)]
     [!code-vb[VSSDKSignatureHelpTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#27)]  
  
5. Zaimplementuj <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodę, aby zawsze przekazywać polecenie.  
  
     [!code-csharp[VSSDKSignatureHelpTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#28)]
     [!code-vb[VSSDKSignatureHelpTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#28)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>Implementowanie dostawcy poleceń pomocy dotyczącej podpisu  
 Możesz podać polecenie pomocy do podpisu, implementując <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> procedurę obsługi poleceń podczas tworzenia widoku tekstu.  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>Aby zaimplementować dostawcę poleceń pomocy dla podpisu  
  
1. Dodaj klasę o nazwie `TestSignatureHelpController` implementującą <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> i wyeksportuj ją z <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> i <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#29)]
     [!code-vb[VSSDKSignatureHelpTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#29)]  
  
2. Zaimportuj <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (używany do uzyskania <xref:Microsoft.VisualStudio.Text.Editor.ITextView> , pod względem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> obiektu), <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (używany do znalezienia bieżącego wyrazu) i <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (aby wyzwolić sesję pomocy dla podpisu).  
  
     [!code-csharp[VSSDKSignatureHelpTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#30)]
     [!code-vb[VSSDKSignatureHelpTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#30)]  
  
3. Zaimplementuj <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metodę, tworząc wystąpienie elementu `TestSignatureCommandHandler` .  
  
     [!code-csharp[VSSDKSignatureHelpTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#31)]
     [!code-vb[VSSDKSignatureHelpTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#31)]  
  
## <a name="building-and-testing-the-code"></a>Kompilowanie i testowanie kodu  
 Aby przetestować ten kod, skompiluj rozwiązanie SignatureHelpTest i uruchom je w eksperymentalnym wystąpieniu.  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Aby skompilować i przetestować rozwiązanie SignatureHelpTest  
  
1. Skompiluj rozwiązanie.  
  
2. Po uruchomieniu tego projektu w debugerze tworzone jest drugie wystąpienie programu Visual Studio.  
  
3. Utwórz plik tekstowy i wpisz tekst zawierający wyraz "Add" oraz nawias otwierający.  
  
4. Po wpisaniu nawiasu otwierającego powinna zostać wyświetlona etykietka narzędzia, która wyświetla listę dwóch podpisów dla `add()` metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
