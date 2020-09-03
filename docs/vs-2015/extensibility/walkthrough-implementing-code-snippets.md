---
title: 'Przewodnik: implementowanie fragmentów kodu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb720589bc9bc31b7cf2a04b05559cb9c9d46961
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201979"
---
# <a name="walkthrough-implementing-code-snippets"></a>Przewodnik: implementowanie fragmentów kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można utworzyć fragmenty kodu i dołączyć je do rozszerzenia edytora, aby użytkownicy rozszerzenia mogli dodawać je do własnego kodu.  
  
 Fragment kodu jest fragmentem kodu lub innym tekstem, który można dołączyć do pliku. Aby wyświetlić wszystkie fragmenty kodu, które zostały zarejestrowane dla określonych języków programowania, w menu **Narzędzia** kliknij polecenie **Menedżer fragmentów kodu**. Aby wstawić fragment kodu do pliku, kliknij prawym przyciskiem myszy w miejscu, w którym chcesz umieścić fragment kodu, kliknij polecenie **Wstaw fragment kodu** lub **Otocz za pomocą**, Znajdź odpowiedni fragment kodu, a następnie kliknij go dwukrotnie. Naciśnij klawisz TAB lub SHIFT + TAB, aby zmodyfikować odpowiednie fragmenty fragmentu kodu, a następnie naciśnij klawisz ENTER lub ESC, aby je zaakceptować. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](../ide/code-snippets.md).  
  
 Fragment kodu jest zawarty w pliku XML, który ma rozszerzenie nazwy pliku. fragment. Fragment kodu może zawierać pola, które są wyróżnione po wstawieniu wstawki, aby użytkownik mógł je znaleźć i zmienić. Plik wstawki zawiera również informacje dotyczące **Menedżera fragmentów kodu** , aby można było wyświetlić nazwę fragmentu w prawidłowej kategorii. Aby uzyskać więcej informacji na temat schematu fragmentu kodu, zobacz [odwołania do schematu](../ide/code-snippets-schema-reference.md).  
  
 W tym instruktażu przedstawiono sposób wykonywania następujących zadań:  
  
1. Utwórz i zarejestruj fragmenty kodu dla określonego języka.  
  
2. Dodaj polecenie **Wstaw fragment kodu** do menu skrótów.  
  
3. Zaimplementuj rozszerzenie fragmentu kodu.  
  
   Ten przewodnik jest oparty na [przewodniku: wyświetlanie uzupełniania instrukcji](../extensibility/walkthrough-displaying-statement-completion.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-and-registering-code-snippets"></a>Tworzenie i rejestrowanie fragmentów kodu  
 Zwykle fragmenty kodu są skojarzone z zarejestrowanej usługi językowej. Nie trzeba jednak wdrażać programu <xref:Microsoft.VisualStudio.Package.LanguageService> w celu zarejestrowania fragmentów kodu. Zamiast tego wystarczy określić identyfikator GUID w pliku indeksu fragmentu kodu, a następnie użyć tego samego identyfikatora GUID w elemencie <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> , który zostanie dodany do projektu.  
  
 Poniższe kroki przedstawiają sposób tworzenia fragmentów kodu i kojarzenia ich z określonym identyfikatorem GUID.  
  
1. Utwórz następującą strukturę katalogów:  
  
    **%InstallDir%\TestSnippets\Snippets\1033\\**  
  
    gdzie *% INSTALLDIR%* jest folderem instalacyjnym programu Visual Studio. (Chociaż ta ścieżka jest zwykle używana do instalowania fragmentów kodu, można określić dowolną ścieżkę).  
  
2. W folderze \ 1033 \ Utwórz plik. XML i nadaj mu nazwę **TestSnippets.xml**. (Chociaż ta nazwa jest zwykle używana w pliku indeksu fragmentu kodu, można określić dowolną nazwę, o ile ma rozszerzenie nazwy pliku. xml). Dodaj następujący tekst, a następnie usuń zastępczy identyfikator GUID i Dodaj własny.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8" ?>  
   <SnippetCollection>  
       <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}">  
           <SnippetDir>  
               <OnOff>On</OnOff>  
               <Installed>true</Installed>  
               <Locale>1033</Locale>  
               <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath>  
               <LocalizedName>Snippets</LocalizedName>  
           </SnippetDir>  
       </Language>  
   </SnippetCollection>  
   ```  
  
3. Utwórz plik w folderze fragmentu, nadaj mu nazwę **test** `.snippet` , a następnie Dodaj następujący tekst:  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8" ?>  
   <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
       <CodeSnippet Format="1.0.0">  
           <Header>  
               <Title>Test replacement fields</Title>  
               <Shortcut>test</Shortcut>  
               <Description>Code snippet for testing replacement fields</Description>  
               <Author>MSIT</Author>  
               <SnippetTypes>  
                   <SnippetType>Expansion</SnippetType>  
               </SnippetTypes>  
           </Header>  
           <Snippet>  
               <Declarations>  
                   <Literal>  
                     <ID>param1</ID>  
                       <ToolTip>First field</ToolTip>  
                       <Default>first</Default>  
                   </Literal>  
                   <Literal>  
                       <ID>param2</ID>  
                       <ToolTip>Second field</ToolTip>  
                       <Default>second</Default>  
                   </Literal>  
               </Declarations>  
               <References>  
                  <Reference>  
                      <Assembly>System.Windows.Forms.dll</Assembly>  
                  </Reference>  
               </References>  
               <Code Language="TestSnippets">  
                   <![CDATA[MessageBox.Show("$param1$");  
        MessageBox.Show("$param2$");]]>  
               </Code>    
           </Snippet>  
       </CodeSnippet>  
   </CodeSnippets>  
   ```  
  
   Poniższe kroki pokazują, jak zarejestrować fragmenty kodu.  
  
#### <a name="to-register-code-snippets-for-a-specific-guid"></a>Aby zarejestrować fragmenty kodu dla określonego identyfikatora GUID  
  
1. Otwórz projekt **CompletionTest** . Aby uzyskać informacje o sposobach tworzenia tego projektu, zobacz [Przewodnik: wyświetlanie uzupełniania instrukcji](../extensibility/walkthrough-displaying-statement-completion.md).  
  
2. W projekcie Dodaj odwołania do następujących zestawów:  
  
    - Microsoft. VisualStudio. TextManager. Interop  
  
    - Microsoft. VisualStudio. TextManager. Interop. 8.0  
  
    - Microsoft. MSXML  
  
3. W projekcie Otwórz plik source. Extension. vsixmanifest.  
  
4. Upewnij się, że karta **zasoby** zawiera typ zawartości **pakietu VSPackage** i że **projekt** jest ustawiony na nazwę projektu.  
  
5. Wybierz projekt CompletionTest, a następnie w okno Właściwości Set **Generate pkgdef File** **.** Zapisz projekt.  
  
6. Dodaj klasę statyczną `SnippetUtilities` do projektu.  
  
     [!code-csharp[VSSDKCompletionTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#22)]
     [!code-vb[VSSDKCompletionTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#22)]  
  
7. W klasie SnippetUtilities zdefiniuj identyfikator GUID i nadaj mu wartość użytą w pliku SnippetsIndex.xml.  
  
     [!code-csharp[VSSDKCompletionTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#23)]
     [!code-vb[VSSDKCompletionTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#23)]  
  
8. Dodaj <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> do `TestCompletionHandler` klasy. Ten atrybut można dodać do dowolnej klasy publicznej lub wewnętrznej (niestatycznej) w projekcie. (Może być konieczne dodanie `using` instrukcji dla przestrzeni nazw Microsoft. VisualStudio. Shell).  
  
     [!code-csharp[VSSDKCompletionTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#24)]
     [!code-vb[VSSDKCompletionTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#24)]  
  
9. Skompiluj i Uruchom projekt. W eksperymentalnym wystąpieniu programu Visual Studio, które zaczyna się, gdy projekt jest uruchomiony, ten fragment kodu, który właśnie zarejestrowałeś, powinien zostać wyświetlony w **Menedżerze fragmentów kodów** w języku **TestSnippets** .  
  
## <a name="adding-the-insert-snippet-command-to-the-shortcut-menu"></a>Dodawanie polecenia Wstaw wstawki do menu skrótów  
 Polecenie **Wstaw fragment kodu** nie jest zawarte w menu skrótów dla pliku tekstowego. W związku z tym należy włączyć polecenie.  
  
#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Aby dodać polecenie Wstaw wstawki do menu skrótów  
  
1. Otwórz `TestCompletionCommandHandler` plik klasy.  
  
     Ponieważ ta klasa implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , można aktywować polecenie **Wstaw fragment kodu** w <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodzie. Przed włączeniem polecenia Sprawdź, czy ta metoda nie jest wywoływana wewnątrz funkcji automatyzacji, ponieważ po kliknięciu polecenia **Wstaw fragment kodu** zostanie wyświetlony interfejs użytkownika selektora fragmentów kodu (UI).  
  
     [!code-csharp[VSSDKCompletionTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#25)]
     [!code-vb[VSSDKCompletionTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#25)]  
  
2. Skompiluj i Uruchom projekt. W eksperymentalnym wystąpieniu Otwórz plik, który ma rozszerzenie nazwy pliku. zzz, a następnie kliknij prawym przyciskiem myszy w dowolnym miejscu. Polecenie **Wstaw fragment kodu** powinno pojawić się w menu skrótów.  
  
## <a name="implementing-snippet-expansion-in-the-snippet-picker-ui"></a>Implementowanie rozszerzenia fragmentu kodu w interfejsie użytkownika selektora fragmentów kodu  
 W tej sekcji pokazano, jak zaimplementować rozszerzenie fragmentu kodu, tak aby interfejs użytkownika selektora fragmentów był wyświetlany po kliknięciu przycisku **Wstaw fragment** w menu skrótów. Fragment kodu jest również rozszerzany, gdy użytkownik wpisze skrót do fragmentu kodu, a następnie naciśnie klawisz TAB.  
  
 Aby wyświetlić interfejs użytkownika selektora fragmentów i włączyć funkcję nawigacji i zatwierdzania fragmentów kodu po wstawieniu, użyj <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody. Samo wstawienie jest obsługiwane przez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> metodę.  
  
 Implementacja rozszerzenia fragmentu kodu używa starszych <xref:Microsoft.VisualStudio.TextManager.Interop> interfejsów. W przypadku tłumaczenia z bieżących klas edytora do starszego kodu, należy pamiętać, że starsze interfejsy używają kombinacji numerów wierszy i numerów kolumn do określania lokalizacji w buforze tekstowym, ale bieżące klasy używają jednego indeksu. W związku z tym, jeśli bufor ma trzy wiersze, z których każdy ma dziesięć znaków (plus, który liczy jako 1 znak), czwarty znak w trzecim wierszu znajduje się na pozycji 27 bieżącej implementacji, ale znajduje się w wierszu 2, pozycja 3 w starej implementacji.  
  
#### <a name="to-implement-snippet-expansion"></a>Aby zaimplementować rozszerzenie fragmentu kodu  
  
1. Do pliku, który zawiera `TestCompletionCommandHandler` klasę, Dodaj następujące `using` instrukcje.  
  
     [!code-csharp[VSSDKCompletionTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#26)]
     [!code-vb[VSSDKCompletionTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#26)]  
  
2. Ustaw `TestCompletionCommandHandler` klasę jako implementującą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interfejs.  
  
     [!code-csharp[VSSDKCompletionTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#27)]
     [!code-vb[VSSDKCompletionTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#27)]  
  
3. W `TestCompletionCommandHandlerProvider` klasie zaimportuj <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> .  
  
     [!code-csharp[VSSDKCompletionTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#28)]
     [!code-vb[VSSDKCompletionTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#28)]  
  
4. Dodaj pola prywatne dla interfejsów rozszerzających kod i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .  
  
     [!code-csharp[VSSDKCompletionTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#29)]
     [!code-vb[VSSDKCompletionTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#29)]  
  
5. W konstruktorze `TestCompletionCommandHandler` klasy ustaw następujące pola.  
  
     [!code-csharp[VSSDKCompletionTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#30)]
     [!code-vb[VSSDKCompletionTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#30)]  
  
6. Aby wyświetlić selektor wstawki, gdy użytkownik kliknie polecenie **Wstaw fragment** kodu, Dodaj następujący kod do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody. (Aby to wyjaśnienie było bardziej czytelne, kod wykonywalny (), który jest używany do uzupełniania instrukcji nie jest wyświetlany; zamiast tego bloki kodu są dodawane do istniejącej metody.) Dodaj następujący blok kodu po kodzie, który sprawdza znak.  
  
     [!code-csharp[VSSDKCompletionTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#31)]
     [!code-vb[VSSDKCompletionTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#31)]  
  
7. Jeśli fragment kodu zawiera pola, które mogą być przechodzenie, sesja rozszerzania jest otwarta do momentu, gdy rozszerzanie zostanie jawnie zaakceptowane; Jeśli fragment kodu nie zawiera żadnych pól, sesja jest zamknięta i jest zwracana `null` przez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> metodę. W <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodzie, po kodzie interfejsu użytkownika selektora fragmentów, który został dodany w poprzednim kroku, Dodaj następujący kod, aby obsłużyć nawigację fragmentu (gdy użytkownik naciśnie klawisz TAB lub Shift + Tab po wstawieniu fragmentu kodu).  
  
     [!code-csharp[VSSDKCompletionTest#32](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#32)]
     [!code-vb[VSSDKCompletionTest#32](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#32)]  
  
8. Aby wstawić fragment kodu, gdy użytkownik wpisze odpowiedni skrót, a następnie naciśnij klawisz TAB, Dodaj kod do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody. Metoda prywatna, która wstawia fragment kodu, zostanie wyświetlona w późniejszym kroku. Dodaj następujący kod po kodzie nawigacji, który został dodany w poprzednim kroku.  
  
     [!code-csharp[VSSDKCompletionTest#33](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#33)]
     [!code-vb[VSSDKCompletionTest#33](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#33)]  
  
9. Zaimplementuj metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interfejsu. W tej implementacji jedyną metodą zainteresowania są <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> . Pozostałe metody powinny po prostu zwrócić <xref:Microsoft.VisualStudio.VSConstants.S_OK> .  
  
     [!code-csharp[VSSDKCompletionTest#34](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#34)]
     [!code-vb[VSSDKCompletionTest#34](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#34)]  
  
10. Zaimplementuj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> metodę. Metoda pomocnika, która wstawia rozszerzenia, zostanie uwzględniona w późniejszym kroku. <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>Zawiera informacje o wierszu i kolumnie, które można uzyskać od <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .  
  
     [!code-csharp[VSSDKCompletionTest#35](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#35)]
     [!code-vb[VSSDKCompletionTest#35](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#35)]  
  
11. Poniższa metoda prywatna wstawia fragment kodu na podstawie skrótu lub tytułu i ścieżki. Następnie wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> metodę za pomocą fragmentu kodu.  
  
     [!code-csharp[VSSDKCompletionTest#36](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#36)]
     [!code-vb[VSSDKCompletionTest#36](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#36)]  
  
## <a name="building-and-testing-code-snippet-expansion"></a>Kompilowanie i testowanie rozwinięcia fragmentu kodu  
 Możesz sprawdzić, czy rozszerzenie fragmentu działa w projekcie.  
  
1. Skompiluj rozwiązanie. Po uruchomieniu tego projektu w debugerze tworzone jest drugie wystąpienie programu Visual Studio.  
  
2. Otwórz plik tekstowy i wpisz tekst.  
  
3. Kliknij prawym przyciskiem myszy w tekście, a następnie kliknij **Wstaw fragment kodu**.  
  
4. Interfejs użytkownika selektora fragmentów powinien pojawić się z wyskakującym menu zawierającym **pola zastępujące testy**. Kliknij dwukrotnie wyskakujące okienko.  
  
     Należy wstawić poniższy fragment kodu.  
  
    ```  
    MessageBox.Show("first");  
    MessageBox.Show("second");  
    ```  
  
     Nie naciskaj klawisza ENTER ani ESC.  
  
5. Naciśnij klawisz TAB i klawisze SHIFT + TAB, aby przełączać się między elementami "First" i "Second".  
  
6. Zaakceptuj Wstawianie, naciskając klawisz ENTER lub ESC.  
  
7. W innej części tekstu wpisz "test", a następnie naciśnij klawisz TAB. Ponieważ "test" jest skrótem fragmentu kodu, fragment powinien zostać wstawiony ponownie.  
  
## <a name="next-steps"></a>Następne kroki
