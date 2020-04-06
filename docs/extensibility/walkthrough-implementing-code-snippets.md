---
title: 'Przewodnik: Implementowanie fragmentów kodu | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: ba1b6e0852c1ec1b306938b791eed78e79d211ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697098"
---
# <a name="walkthrough-implement-code-snippets"></a>Instruktaż: Implementowanie fragmentów kodu
Można utworzyć fragmenty kodu i dołączyć je do rozszerzenia edytora, dzięki czemu użytkownicy rozszerzenia mogą dodać je do własnego kodu.

 Fragment kodu jest fragment kodu lub inny tekst, który może być włączony do pliku. Aby wyświetlić wszystkie urywki, które zostały zarejestrowane dla określonych języków programowania, w menu **Narzędzia** kliknij polecenie **Menedżer fragmentów kodu**. Aby wstawić fragment kodu do pliku, kliknij prawym przyciskiem myszy miejsce, w którym ma być fragment kodu, kliknij polecenie Wstaw fragment kodu lub **Za pomocą przycisku Surround With**, znajdź odpowiedni urywek, a następnie kliknij go dwukrotnie. Naciśnij **klawisz Tab** lub Klawisz **Shift**+**Tab,** aby zmodyfikować odpowiednie części fragmentu kodu, a następnie naciśnij klawisz **Enter** lub **Esc,** aby go zaakceptować. Aby uzyskać więcej informacji, zobacz [Fragmenty kodu](../ide/code-snippets.md).

 Fragment kodu znajduje się w pliku XML z rozszerzeniem nazwy pliku .snippet*. Fragment kodu może zawierać pola, które są wyróżnione po wstawieniu fragmentu kodu, aby użytkownik mógł je znaleźć i zmienić. Plik urywka zawiera również informacje dotyczące **Menedżera fragmentów kodu,** dzięki czemu może wyświetlać nazwę fragmentu kodu w odpowiedniej kategorii. Aby uzyskać informacje na temat schematu fragmentu kodu, zobacz [Odwołanie do fragmentów kodu](../ide/code-snippets-schema-reference.md).

 W tym przewodniku uczy się, jak wykonać następujące zadania:

1. Tworzenie i rejestrowanie fragmentów kodu dla określonego języka.

2. Dodaj polecenie **Wstaw fragment kodu** do menu skrótów.

3. Implementowanie rozszerzenia fragmentu kodu.

   Ten instruktaż jest oparty na [instruktażu: Zakończenie instrukcji wyświetlania](../extensibility/walkthrough-displaying-statement-completion.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-and-register-code-snippets"></a>Tworzenie i rejestrowanie fragmentów kodu
 Zazwyczaj fragmenty kodu są skojarzone z zarejestrowaną usługą językową. Jednak nie trzeba zaimplementować <xref:Microsoft.VisualStudio.Package.LanguageService> fragmenty kodu, aby zarejestrować. Zamiast tego wystarczy określić identyfikator GUID w pliku indeksu fragmentu kodu, a następnie użyć tego samego identyfikatora <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> GUID w dodaniu do projektu.

 W poniższych krokach pokazano, jak utworzyć fragmenty kodu i skojarzyć je z określonym identyfikatorem GUID.

1. Utwórz następującą strukturę katalogów:

    **%InstallDir%\TestSnippets\Urywki\1033\\**

    gdzie *%InstallDir%* jest folderem instalacyjnym programu Visual Studio. (Chociaż ta ścieżka jest zwykle używana do instalowania fragmentów kodu, można określić dowolną ścieżkę).

2. W folderze \1033\ utwórz plik *xml* i nazwij go **TestSnippets.xml**. (Mimo że ta nazwa jest zwykle używana dla pliku indeksu fragmentu kodu, można określić dowolną nazwę, o ile ma rozszerzenie nazwy pliku *xml.* Dodaj następujący tekst, a następnie usuń zastępczy identyfikator GUID i dodaj własny.

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

3. Utwórz plik w folderze urywka, nazwij go **testem,**`.snippet`a następnie dodaj następujący tekst:

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

### <a name="to-register-code-snippets-for-a-specific-guid"></a>Aby zarejestrować fragmenty kodu dla określonego identyfikatora GUID

1. Otwórz projekt **CompletionTest.** Aby uzyskać informacje dotyczące tworzenia tego projektu, zobacz [Instruktaż: Zakończenie wyświetlania instrukcji](../extensibility/walkthrough-displaying-statement-completion.md).

2. W projekcie dodaj odwołania do następujących zestawów:

    - Microsoft.VisualStudio.TextManager.Interop

    - Microsoft.VisualStudio.TextManager.Interop.8.0

    - plik microsoft.msxml

3. W projekcie otwórz plik **source.extension.vsixmanifest.**

4. Upewnij się, że **karta Zasoby** zawiera typ zawartości **VsPackage** i że **program Project** jest ustawiony na nazwę projektu.

5. Wybierz projekt CompletionTest i w oknie Właściwości zestaw **Generate Pkgdef File** to **true**. Zapisz projekt.

6. Dodaj klasę `SnippetUtilities` statyczną do projektu.

     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]

7. W klasie Narzędzia urywek zdefiniuj identyfikator GUID i nadaj mu wartość używaną w pliku *SnippetsIndex.xml.*

     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]

8. Dodaj <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> do `TestCompletionHandler` klasy. Ten atrybut można dodać do dowolnej klasy publicznej lub wewnętrznej (niestatyczne) w projekcie. (Może być trzeba `using` dodać dyrektywę dla obszaru nazw Microsoft.VisualStudio.Shell.)

     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]

9. Tworzenie i uruchamianie projektu. W eksperymentalnym wystąpieniu programu Visual Studio, który rozpoczyna się po uruchomieniu projektu, fragment kodu, który właśnie zarejestrowałeś, powinien być wyświetlany w **Menedżerze urywków kodu** w języku **TestSnippets.**

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>Dodawanie polecenia Wstaw fragment kodu do menu skrótów
 Polecenie **Wstaw fragment** kodu nie znajduje się w menu skrótów pliku tekstowego. W związku z tym należy włączyć polecenie.

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Aby dodać polecenie Wstaw fragment kodu do menu skrótów

1. Otwórz `TestCompletionCommandHandler` plik klasy.

     Ponieważ ta klasa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>implementuje, można aktywować **polecenie Wstaw urywek** w metodzie. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Przed włączeniem polecenia sprawdź, czy ta metoda nie jest wywoływana wewnątrz funkcji automatyzacji, ponieważ po kliknięciu polecenia Wstaw urywek wyświetla interfejs użytkownika selektora urywków.Before you enable the command, check that this method is not being called inside an automation function because when the **Insert Snippet** command is clicked, it displays the 000ppet picker user interface (UI).

     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]

2. Tworzenie i uruchamianie projektu. W eksperymentalnym wystąpieniu otwórz plik z rozszerzeniem nazwy pliku *.zzz,* a następnie kliknij prawym przyciskiem myszy w dowolnym miejscu. Polecenie **Wstaw fragment** powinien pojawić się w menu skrótów.

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>Implementowanie rozszerzenia fragmentu kodu w interfejsie użytkownika selektora urywek
 W tej sekcji pokazano, jak zaimplementować rozszerzenie fragmentu kodu, tak aby interfejs użytkownika selektora fragmentów kodu był wyświetlany po kliknięciu w menu skrótów **wstawiania fragmentu kodu.** Fragment kodu jest również rozwijany, gdy użytkownik wpisuje skrót do fragmentu kodu, a następnie naciśnie **klawisz Tab**.

 Aby wyświetlić interfejs użytkownika selektora fragmentów kodu i włączyć akceptację fragmentu kodu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> nawigacji i po wstawieniu, należy użyć tej metody. Samo wstawienie jest <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> obsługiwane przez metodę.

 Implementacja rozszerzenia fragmentu kodu używa <xref:Microsoft.VisualStudio.TextManager.Interop> starszych interfejsów. Podczas tłumaczenia z bieżących klas edytora do starszego kodu, należy pamiętać, że starsze interfejsy używają kombinacji numerów wierszy i numerów kolumn, aby określić lokalizacje w buforze tekstowym, ale bieżące klasy używają jednego indeksu. W związku z tym jeśli bufor ma trzy wiersze, z których każdy ma 10 znaków (plus nowy wiersz, który liczy się jako jeden znak), czwarty znak w trzecim wierszu znajduje się na pozycji 27 w bieżącej implementacji, ale znajduje się w wierszu 2, pozycja 3 w starej implementacji.

#### <a name="to-implement-snippet-expansion"></a>Aby zaimplementować rozszerzenie fragmentu kodu

1. Do pliku, który `TestCompletionCommandHandler` zawiera klasę, `using` dodaj następujące dyrektywy.

     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]

2. Upewnij `TestCompletionCommandHandler` się, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> że klasa implementuje interfejs.

     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]

3. W `TestCompletionCommandHandlerProvider` klasie zaimportuj plik <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>.

     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]

4. Dodaj kilka pól prywatnych dla interfejsów rozszerzenia kodu i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.

     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]

5. W konstruktorze `TestCompletionCommandHandler` klasy ustaw następujące pola.

     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]

6. Aby wyświetlić selektor urywków, gdy użytkownik kliknie polecenie **Wstaw urywek,** dodaj do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody następujący kod. (Aby to wyjaśnienie było bardziej `Exec()`czytelne, kod, który jest używany do uzupełniania instrukcji nie jest wyświetlany; zamiast tego bloki kodu są dodawane do istniejącej metody.) Dodaj następujący blok kodu po kodzie, który sprawdza znak.

     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]

7. Jeśli fragment kodu ma pola, które można nawigować, sesja rozszerzenia jest otwarta, dopóki rozszerzenie nie zostanie jawnie zaakceptowane; Jeśli fragment kodu nie ma pól, sesja jest zamykana i zwracana jako `null` metoda. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> W <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodzie po kod interfejsu użytkownika selektora fragmentów kodu, który został dodany w poprzednim kroku, dodaj następujący kod do obsługi nawigacji fragmentu kodu (gdy użytkownik naciśnie **Tab** lub **Shift**+**Tab** po wstawieniu fragmentu).

     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]

8. Aby wstawić fragment kodu, gdy użytkownik wpisze odpowiedni skrót, a następnie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> naciśnie klawisz **Tab**, dodaj kod do metody. Metoda prywatna, która wstawia fragment kodu, zostanie wyświetlona w późniejszym kroku. Dodaj następujący kod po kodzie nawigacyjnym dodanym w poprzednim kroku.

     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]

9. Zaimplementuj metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interfejsu. W tej realizacji jedynymi metodami zainteresowania są <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Inne metody powinny <xref:Microsoft.VisualStudio.VSConstants.S_OK>po prostu powrócić .

     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]

10. Zaimplementuj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> metodę. Metoda pomocnika, która faktycznie wstawia rozszerzenia jest omówiona w późniejszym kroku. Zawiera <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> informacje o wierszu i kolumnie, które można uzyskać z pliku <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.

     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]

11. Następująca metoda prywatna wstawia fragment kodu, oparty na skrótze lub na tytule i ścieżce. Następnie wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> metodę z fragmentem kodu.

     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]

## <a name="build-and-test-code-snippet-expansion"></a>Tworzenie i testowanie rozszerzenia fragmentu kodu
 Można sprawdzić, czy rozszerzenie fragmentu kodu działa w projekcie.

1. Skompiluj rozwiązanie. Po uruchomieniu tego projektu w debugerze zostanie uruchomione drugie wystąpienie programu Visual Studio.

2. Otwórz plik tekstowy i wpisz tekst.

3. Kliknij prawym przyciskiem myszy miejsce w tekście, a następnie kliknij polecenie **Wstaw fragment kodu**.

4. Interfejs użytkownika selektora fragmentów kodu powinien pojawić się z wyskakującym okienkiem z **napisem Test pola wymiany**. Kliknij dwukrotnie okno podręczne.

     Należy wstawić następujący fragment kodu.

    ```
    MessageBox.Show("first");
    MessageBox.Show("second");
    ```

     Nie **naciskaj klawiszy Enter** lub **Esc**.

5. Naciśnij **klawisz Tab** i klawisz **Shift**+**Tab,** aby przełączać się między "pierwszym" a "drugim".

6. Zaakceptuj wstawienie, naciskając **klawisz Enter** lub **Esc**.

7. W innej części tekstu wpisz "test", a następnie naciśnij **klawisz Tab**. Ponieważ "test" jest skrótem fragmentu kodu, fragment kodu powinien zostać ponownie wstawiony.

## <a name="next-steps"></a>Następne kroki
