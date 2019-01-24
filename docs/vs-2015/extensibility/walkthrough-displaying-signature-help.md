---
title: 'Przewodnik: Wyświetlanie pomocy dotyczącej sygnatur | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 8a5f62ace3126ee35f47a90c15e6183690786954
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54781222"
---
# <a name="walkthrough-displaying-signature-help"></a>Przewodnik: Wyświetlanie pomocy dotyczącej podpisów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocy dotyczącej sygnatur (znany także jako *Parameter Info*) Wyświetla podpis metody w etykietce narzędzia, gdy użytkownik wpisuje znak start listy parametrów (zazwyczaj nawias otwierający). Jako parametr i separator parametru (zazwyczaj przecinek) mają typ, etykietki narzędzia jest aktualizowana w celu wyświetlenia następny parametr pogrubioną czcionką. Pomoc podpisu można zdefiniować w kontekście usługi językowej, można zdefiniować własny plik Nazwa rozszerzenia i zawartości typ i wyświetlić Pomoc podpisu dla właśnie tego typu lub możesz wyświetlić Pomoc podpisu dla istniejącego typu zawartości (na przykład "text"). Ten poradnik pokazuje jak wyświetlić Pomoc podpisu dla typu zawartości "text".  
  
 Pomocy dotyczącej sygnatur zwykle jest wyzwalany przez wpisanie określonych znaków, na przykład, "(" (nawias otwierający), a zostanie odrzucony, wpisując znak inny, na przykład, ")" (zamykający nawias). Funkcje IntelliSense, które są wyzwalane, wpisując znak można zaimplementować przy użyciu procedurę obsługi poleceń dla naciśnięcia klawiszy ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu) i dostawcy programu obsługi, który implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfejsu. Aby utworzyć źródło pomoc podpisu, czyli wykaz sygnatur, które uczestniczą w pomoc podpisu, należy zaimplementować <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> interfejsu i dostawcy źródła, który implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> interfejsu. Dostawcy są składnikami Managed Extensibility Framework (MEF) i odpowiadają za eksportowanie klas źródłowych i kontrolera i importowanie usługi i brokerzy, na przykład <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, który umożliwia nawigowanie w buforze tekstu i <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, która wyzwala sesji pomoc podpisu.  
  
 W tym instruktażu pokazano, jak zaimplementować pomoc podpisu stały zestaw identyfikatorów. W pełnej implementacji język jest odpowiedzialne za świadczenie tej zawartości.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Tworzenie projektu MEF  
  
#### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF  
  
1.  Utwórz projekt VSIX języka C#. (W **nowy projekt** okno dialogowe, wybierz opcję **Visual C# / rozszerzalności**, następnie **projekt VSIX**.) Nazwij rozwiązanie `SignatureHelpTest`.  
  
2.  Dodaj szablon elementu edytora klasyfikatora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Usuń istniejące pliki klasy.  
  
4.  Dodaj następujące odwołania do projektu i upewnij się, **CopyLocal** ustawiono `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>Implementowanie podpisu podpisów i parametry  
 Źródło pomoc podpisu opiera się na podpisy, które implementują <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, z których każdy zawiera parametry, które implementują <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>. W pełnej implementacji będzie można uzyskać te informacje w dokumentacji języka, ale w tym przykładzie podpisy są zakodowane.  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Aby zaimplementować podpisów pomoc podpisu i parametry  
  
1.  Dodaj plik klasy i nadaj mu nazwę `SignatureHelpSource`.  
  
2.  Dodaj następujące instrukcje importu.  
  
     [!code-csharp[VSSDKSignatureHelpTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#1)]
     [!code-vb[VSSDKSignatureHelpTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#1)]  
  
3.  Dodaj klasę o nazwie `TestParameter` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#2)]
     [!code-vb[VSSDKSignatureHelpTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#2)]  
  
4.  Dodaj Konstruktor, który ustawia wszystkie właściwości.  
  
     [!code-csharp[VSSDKSignatureHelpTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#3)]
     [!code-vb[VSSDKSignatureHelpTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#3)]  
  
5.  Dodawanie właściwości <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#4)]
     [!code-vb[VSSDKSignatureHelpTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#4)]  
  
6.  Dodaj klasę o nazwie `TestSignature` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#5)]
     [!code-vb[VSSDKSignatureHelpTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#5)]  
  
7.  Dodaj kilka pól prywatnych.  
  
     [!code-csharp[VSSDKSignatureHelpTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#6)]
     [!code-vb[VSSDKSignatureHelpTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#6)]  
  
8.  Dodaj Konstruktor, który ustawia pola i subskrybuje <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzeń.  
  
     [!code-csharp[VSSDKSignatureHelpTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#7)]
     [!code-vb[VSSDKSignatureHelpTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#7)]  
  
9. Zadeklaruj `CurrentParameterChanged` zdarzeń. To zdarzenie jest wywoływane, gdy użytkownik wprowadza w jeden z parametrów w podpisie.  
  
     [!code-csharp[VSSDKSignatureHelpTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#8)]
     [!code-vb[VSSDKSignatureHelpTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#8)]  
  
10. Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> właściwości, tak że zgłasza `CurrentParameterChanged` zdarzenie, gdy wartość właściwości została zmieniona.  
  
     [!code-csharp[VSSDKSignatureHelpTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#9)]
     [!code-vb[VSSDKSignatureHelpTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#9)]  
  
11. Dodaj metodę, która wywołuje `CurrentParameterChanged` zdarzeń.  
  
     [!code-csharp[VSSDKSignatureHelpTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#10)]
     [!code-vb[VSSDKSignatureHelpTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#10)]  
  
12. Dodaj metodę, która oblicza bieżącego parametru przez porównywanie liczba przecinków w <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> do liczby przecinkami w podpisie.  
  
     [!code-csharp[VSSDKSignatureHelpTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#11)]
     [!code-vb[VSSDKSignatureHelpTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#11)]  
  
13. Dodawanie obsługi zdarzeń dla <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzeń, który wywołuje `ComputeCurrentParameter()` metody.  
  
     [!code-csharp[VSSDKSignatureHelpTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#12)]
     [!code-vb[VSSDKSignatureHelpTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#12)]  
  
14. Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> właściwości. Tej właściwości jest przechowywana <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , który odpowiada fragment tekstu w buforze, do której stosują się podpis.  
  
     [!code-csharp[VSSDKSignatureHelpTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#13)]
     [!code-vb[VSSDKSignatureHelpTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#13)]  
  
15. Zaimplementuj inne parametry.  
  
     [!code-csharp[VSSDKSignatureHelpTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#14)]
     [!code-vb[VSSDKSignatureHelpTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#14)]  
  
## <a name="implementing-the-signature-help-source"></a>Implementowanie źródłowego pomoc podpisu  
 Źródło pomoc podpisu jest zestaw podpisów, dla których użytkownik poda informacje.  
  
#### <a name="to-implement-the-signature-help-source"></a>Aby zaimplementować źródła pomoc podpisu  
  
1.  Dodaj klasę o nazwie `TestSignatureHelpSource` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#15)]
     [!code-vb[VSSDKSignatureHelpTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#15)]  
  
2.  Dodaj odwołanie do buforu tekstowego.  
  
     [!code-csharp[VSSDKSignatureHelpTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#16)]
     [!code-vb[VSSDKSignatureHelpTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#16)]  
  
3.  Dodaj Konstruktor, który ustawia bufor tekstowy i dostawcy źródła pomoc podpisu.  
  
     [!code-csharp[VSSDKSignatureHelpTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#17)]
     [!code-vb[VSSDKSignatureHelpTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#17)]  
  
4.  Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> metody. W tym przykładzie podpisy są zakodowane, ale w pełną implementację może uzyskać te informacje w dokumentacji języka.  
  
     [!code-csharp[VSSDKSignatureHelpTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#18)]
     [!code-vb[VSSDKSignatureHelpTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#18)]  
  
5.  Metoda pomocnika `CreateSignature()` znajduje się tylko do celów ilustracyjnych.  
  
     [!code-csharp[VSSDKSignatureHelpTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#19)]
     [!code-vb[VSSDKSignatureHelpTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#19)]  
  
6.  Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> metody. W tym przykładzie istnieją tylko dwa podpisów, z których każdy ma dwa parametry. W związku z tym ta metoda nie jest wymagane. W implementacji większy, w której więcej niż jedno źródło pomoc podpisu jest dostępny, ta metoda jest używana do określania, czy źródło pomoc podpisu najwyższy priorytet, można podać pasujący podpis. Jeśli jest ona nieosiągalna, metoda zwraca wartość null, a źródło dalej najwyższym priorytecie jest monitowany o podanie dopasowania.  
  
     [!code-csharp[VSSDKSignatureHelpTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#20)]
     [!code-vb[VSSDKSignatureHelpTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#20)]  
  
7.  Implementacja metody Dispose():  
  
     [!code-csharp[VSSDKSignatureHelpTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#21)]
     [!code-vb[VSSDKSignatureHelpTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#21)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>Implementowanie dostawcy źródła pomocy podpisu  
 Dostawca źródła pomoc podpisu jest odpowiedzialny za eksportowanie części składnika Managed Extensibility Framework (MEF) i utworzenie wystąpienia źródła pomoc podpisu.  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>Do implementowania dostawcy źródła pomoc podpisu  
  
1.  Dodaj klasę o nazwie `TestSignatureHelpSourceProvider` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>i wyeksportuj go z <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> z "text" i <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> z wcześniej = "default".  
  
     [!code-csharp[VSSDKSignatureHelpTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#22)]
     [!code-vb[VSSDKSignatureHelpTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#22)]  
  
2.  Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> przez utworzenie wystąpienia `TestSignatureHelpSource`.  
  
     [!code-csharp[VSSDKSignatureHelpTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#23)]
     [!code-vb[VSSDKSignatureHelpTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#23)]  
  
## <a name="implementing-the-command-handler"></a>Implementowanie obsługi poleceń  
 Pomocy dotyczącej sygnatur zwykle jest wyzwalany przez (znak i odrzuconych przez) znaków. Możesz obsłużyć naciśnięcia poprzez implementację <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> tak, aby wyzwala pomoc podpisu sesji, gdy odbierze (znak poprzedzony przez nazwę metody znane i odrzuci sesji, gdy odbierze) znaków.  
  
#### <a name="to-implement-the-command-handler"></a>Aby zaimplementować program obsługi poleceń  
  
1.  Dodaj klasę o nazwie `TestSignatureHelpCommand` implementującej <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#24)]
     [!code-vb[VSSDKSignatureHelpTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#24)]  
  
2.  Dodaj pola prywatne dla <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> karty (co pozwala dodać program obsługi poleceń do obsługi łańcucha poleceń), widoku tekstu, pomoc podpisu broker i sesji, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, a następnie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#25)]
     [!code-vb[VSSDKSignatureHelpTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#25)]  
  
3.  Dodaj Konstruktor do zainicjować te pola i Dodaj filtr polecenia do filtrów służbowej.  
  
     [!code-csharp[VSSDKSignatureHelpTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#26)]
     [!code-vb[VSSDKSignatureHelpTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#26)]  
  
4.  Implementowanie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodę, aby wyzwolić pomoc podpisu sesji, gdy odbierze filtr polecenia (znak po jednej nazwy metod znanych i zamknąć sesji, gdy odbierze) znak, podczas gdy sesja jest nadal aktywne. W każdym przypadku polecenia są przekazywane.  
  
     [!code-csharp[VSSDKSignatureHelpTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#27)]
     [!code-vb[VSSDKSignatureHelpTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#27)]  
  
5.  Implementowanie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodę, tak aby zawsze przekazuje polecenia.  
  
     [!code-csharp[VSSDKSignatureHelpTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#28)]
     [!code-vb[VSSDKSignatureHelpTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#28)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>Implementowanie dostawcy polecenia Pomoc podpisu  
 Możesz podać polecenia Pomoc podpisu, implementując <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> utworzyć program obsługi poleceń podczas tworzenia widoku tekstu.  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>Do implementowania dostawcy polecenia Pomoc podpisu  
  
1.  Dodaj klasę o nazwie `TestSignatureHelpController` implementującej <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> i wyeksportuj go z <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, i <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#29)]
     [!code-vb[VSSDKSignatureHelpTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#29)]  
  
2.  Importowanie <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (używane do uzyskania <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, danego <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> obiektu), <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (używana do znajdowania bieżącego słowa) i <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (w celu wyzwolenia pomoc podpisu sesji).  
  
     [!code-csharp[VSSDKSignatureHelpTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#30)]
     [!code-vb[VSSDKSignatureHelpTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#30)]  
  
3.  Implementowanie <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metoda przez utworzenie wystąpienia `TestSignatureCommandHandler`.  
  
     [!code-csharp[VSSDKSignatureHelpTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#31)]
     [!code-vb[VSSDKSignatureHelpTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#31)]  
  
## <a name="building-and-testing-the-code"></a>Tworzenie i testowanie kodu  
 Aby przetestować ten kod, Kompiluj rozwiązanie SignatureHelpTest, a następnie uruchomić go w doświadczalnym wystąpieniu.  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Aby skompilować i przetestować rozwiązanie SignatureHelpTest  
  
1.  Skompiluj rozwiązanie.  
  
2.  Po uruchomieniu tego projektu w debugerze drugiego wystąpienia programu Visual Studio jest uruchomiony.  
  
3.  Utwórz plik tekstowy i wpisz jakiś tekst, który zawiera wyraz "add" oraz nawias otwierający.  
  
4.  Po wpisaniu nawiasu otwierającego, powinien zostać wyświetlony etykietkę narzędzia, która wyświetla listę dwóch sygnatury `add()` metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
