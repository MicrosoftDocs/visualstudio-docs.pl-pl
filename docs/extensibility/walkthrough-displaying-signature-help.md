---
title: 'Przewodnik: Wyświetlanie pomocy dotyczącej sygnatur | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89d81ee2e860dead62352cc14cef95e21536c29d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60105327"
---
# <a name="walkthrough-display-signature-help"></a>Przewodnik: Wyświetlanie pomocy dotyczącej sygnatur
Pomocy dotyczącej sygnatur (znany także jako *Parameter Info*) Wyświetla podpis metody w etykietce narzędzia, gdy użytkownik wpisuje znak start listy parametrów (zazwyczaj nawias otwierający). Jako parametr i separator parametru (zazwyczaj przecinek) mają typ, etykietki narzędzia jest aktualizowana w celu wyświetlenia następny parametr pogrubioną czcionką. Pomoc podpisu można zdefiniować w następujący sposób: w kontekście usługi językowej zdefiniować własne rozszerzenia nazwy pliku i typu zawartości i wyświetlić Pomoc podpisu dla właśnie tego typu lub Wyświetl Pomoc podpisu dla istniejącego typu zawartości (na przykład "text"). Ten poradnik pokazuje jak wyświetlić Pomoc podpisu dla typu zawartości "text".

 Pomocy dotyczącej sygnatur zwykle jest wyzwalany przez wpisanie określonych znaków, na przykład, "(" (nawias otwierający), a zostanie odrzucony, wpisując znak inny, na przykład, ")" (zamykający nawias). Funkcje IntelliSense, które są wyzwalane, wpisując znak można zaimplementować przy użyciu procedurę obsługi poleceń dla naciśnięcia klawiszy ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu) i dostawcy programu obsługi, który implementuje <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfejsu. Aby utworzyć źródło pomoc podpisu, czyli wykaz sygnatur, które uczestniczą w pomoc podpisu, należy zaimplementować <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> interfejsu i dostawcą źródłowego, który działa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> interfejsu. Dostawcy są składnikami Managed Extensibility Framework (MEF) i odpowiadają za eksportowanie klas źródłowych i kontrolera i importowanie usługi i brokerzy, na przykład <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, który umożliwia nawigowanie w buforze tekstu i <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, która wyzwala sesji pomoc podpisu.

 W tym instruktażu pokazano, jak skonfigurować pomoc podpisu ustaloną zbiór identyfikatorów. W pełnej implementacji język jest odpowiedzialne za świadczenie tej zawartości.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie instaluj programu Visual Studio SDK z Centrum pobierania. Został on uwzględniony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-mef-project"></a>Tworzenie projektu MEF

#### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF

1. Utwórz projekt VSIX języka C#. (W **nowy projekt** okno dialogowe, wybierz opcję **Visual C# / rozszerzalności**, następnie **projekt VSIX**.) Nazwij rozwiązanie `SignatureHelpTest`.

2. Dodaj szablon elementu edytora klasyfikatora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Usuń istniejące pliki klasy.

4. Dodaj następujące odwołania do projektu i upewnij się, **CopyLocal** ustawiono `false`:

     Microsoft.VisualStudio.Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft.VisualStudio.Shell.14.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-signature-help-signatures-and-parameters"></a>Implementowanie podpisów pomoc podpisu i parametry
 Źródło pomoc podpisu opiera się na podpisy, które implementują <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, z których każdy zawiera parametry, które implementują <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>. W pełnej implementacji będzie można uzyskać te informacje w dokumentacji języka, ale w tym przykładzie podpisy są zakodowane.

#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Aby zaimplementować podpisów pomoc podpisu i parametry

1. Dodaj plik klasy i nadaj mu nazwę `SignatureHelpSource`.

2. Dodaj następujące instrukcje importu.

     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]

3. Dodaj klasę o nazwie `TestParameter` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.

     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]

4. Dodaj Konstruktor, który ustawia wszystkie właściwości.

     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]

5. Dodawanie właściwości <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.

     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]

6. Dodaj klasę o nazwie `TestSignature` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.

     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]

7. Dodaj kilka pól prywatnych.

     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]

8. Dodaj Konstruktor, który ustawia pola i subskrybuje <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzeń.

     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]

9. Zadeklaruj `CurrentParameterChanged` zdarzeń. To zdarzenie jest wywoływane, gdy użytkownik wprowadza w jeden z parametrów w podpisie.

     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]

10. Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> właściwości, tak że zgłasza `CurrentParameterChanged` zdarzenie, gdy wartość właściwości została zmieniona.

     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]

11. Dodaj metodę, która wywołuje `CurrentParameterChanged` zdarzeń.

     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]

12. Dodaj metodę, która oblicza bieżącego parametru przez porównywanie liczba przecinków w <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> do liczby przecinkami w podpisie.

     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]

13. Dodawanie obsługi zdarzeń dla <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzeń, który wywołuje `ComputeCurrentParameter()` metody.

     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]

14. Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> właściwości. Tej właściwości jest przechowywana <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , który odpowiada fragment tekstu w buforze, do której stosują się podpis.

     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]

15. Zaimplementuj inne parametry.

     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]

## <a name="implement-the-signature-help-source"></a>Implementowanie źródła pomoc podpisu
 Źródło pomoc podpisu jest zestaw podpisów, dla których użytkownik poda informacje.

#### <a name="to-implement-the-signature-help-source"></a>Aby zaimplementować źródła pomoc podpisu

1. Dodaj klasę o nazwie `TestSignatureHelpSource` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.

     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]

2. Dodaj odwołanie do buforu tekstowego.

     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]

3. Dodaj Konstruktor, który ustawia bufor tekstowy i dostawcy źródła pomoc podpisu.

     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]

4. Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> metody. W tym przykładzie podpisy są zakodowane, ale w pełną implementację może uzyskać te informacje w dokumentacji języka.

     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]

5. Metoda pomocnika `CreateSignature()` znajduje się tylko do celów ilustracyjnych.

     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]

6. Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> metody. W tym przykładzie istnieją tylko dwa podpisów, z których każdy ma dwa parametry. W związku z tym ta metoda nie jest wymagane. W implementacji większy, w której więcej niż jedno źródło pomoc podpisu jest dostępny, ta metoda jest używana do określania, czy źródło pomoc podpisu najwyższy priorytet, można podać pasujący podpis. Jeśli jest ona nieosiągalna, metoda zwraca wartość null, a źródło dalej najwyższym priorytecie jest monitowany o podanie dopasowania.

     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]

7. Implementowanie `Dispose()` metody:

     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]

## <a name="implement-the-signature-help-source-provider"></a>Implementowanie dostawcy źródła pomoc podpisu
 Dostawca źródła pomoc podpisu jest odpowiedzialny za eksportowanie części składnika Managed Extensibility Framework (MEF) i utworzenie wystąpienia źródła pomoc podpisu.

#### <a name="to-implement-the-signature-help-source-provider"></a>Do implementowania dostawcy źródła pomoc podpisu

1. Dodaj klasę o nazwie `TestSignatureHelpSourceProvider` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>i wyeksportuj go z <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> z "text" i <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> z wcześniej = "default".

     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]

2. Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> przez utworzenie wystąpienia `TestSignatureHelpSource`.

     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]

## <a name="implement-the-command-handler"></a>Zaimplementuj program obsługi poleceń
 Zazwyczaj wyzwoleniu pomocy dotyczącej sygnatur nawiasu otwierającego znaku "(" znak i odrzuconych przez nawias zamykający")". Które ułatwią Ci obsługę tych klawiszy, uruchamiając <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> tak, aby wyzwala pomoc podpisu sesji, gdy odbierze ona otwierający znaku nawiasu poprzedzone nazwę metody znane i odrzuci sesji, gdy odbierze ona zamykającego znaku nawiasu.

#### <a name="to-implement-the-command-handler"></a>Aby zaimplementować program obsługi poleceń

1. Dodaj klasę o nazwie `TestSignatureHelpCommand` implementującej <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.

     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]

2. Dodaj pola prywatne dla <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> karty (co pozwala dodać program obsługi poleceń do obsługi łańcucha poleceń), widoku tekstu, pomoc podpisu broker i sesji, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, a następnie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.

     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]

3. Dodaj Konstruktor do zainicjować te pola i Dodaj filtr polecenia do filtrów służbowej.

     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]

4. Implementowanie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodę, aby wyzwolić pomoc podpisu sesji, gdy filtr polecenia odbierze nawias otwierający znaku "(" znak po jednej nazwy metod znanych i zamknąć sesji, gdy odbierze ona nawias zamykający")" gdy sesja jest nadal aktywne. W każdym przypadku polecenia są przekazywane.

     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]

5. Implementowanie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodę, tak aby zawsze przekazuje polecenia.

     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]

## <a name="implement-the-signature-help-command-provider"></a>Implementowanie dostawcy polecenia Pomoc podpisu
 Możesz podać polecenia Pomoc podpisu, implementując <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> utworzyć program obsługi poleceń podczas tworzenia widoku tekstu.

### <a name="to-implement-the-signature-help-command-provider"></a>Do implementowania dostawcy polecenia Pomoc podpisu

1. Dodaj klasę o nazwie `TestSignatureHelpController` implementującej <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> i wyeksportuj go z <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, i <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.

     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]

2. Importowanie <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (używane do uzyskania <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, danego <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> obiektu), <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (używana do znajdowania bieżącego słowa) i <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (w celu wyzwolenia pomoc podpisu sesji).

     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]

3. Implementowanie <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metoda przez utworzenie wystąpienia `TestSignatureCommandHandler`.

     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]

## <a name="build-and-test-the-code"></a>Tworzenie i testowanie kodu
 Aby przetestować ten kod, Kompiluj rozwiązanie SignatureHelpTest, a następnie uruchomić go w doświadczalnym wystąpieniu.

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Aby skompilować i przetestować rozwiązanie SignatureHelpTest

1. Skompiluj rozwiązanie.

2. Po uruchomieniu tego projektu w debugerze, drugie wystąpienie programu Visual Studio został uruchomiony.

3. Utwórz plik tekstowy i wpisz jakiś tekst, który zawiera wyraz "add" oraz nawias otwierający.

4. Po wpisaniu nawiasu otwierającego, powinien zostać wyświetlony etykietkę narzędzia, która wyświetla listę dwóch sygnatury `add()` metody.

## <a name="see-also"></a>Zobacz także
- [Przewodnik: Połączyć typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)