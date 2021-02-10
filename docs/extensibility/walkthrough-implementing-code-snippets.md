---
title: 'Przewodnik: implementowanie fragmentów kodu | Microsoft Docs'
description: Można utworzyć fragmenty kodu i dołączyć je do rozszerzenia edytora. Dowiedz się, jak tworzyć/rejestrować fragmenty kodu za pomocą tego przewodnika.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: acangialosi
ms.author: anthc
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: cd01ba1196c75589c0f8844c6bfccab88772ffe4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961719"
---
# <a name="walkthrough-implement-code-snippets"></a>Przewodnik: implementowanie fragmentów kodu
Można utworzyć fragmenty kodu i dołączyć je do rozszerzenia edytora, aby użytkownicy rozszerzenia mogli dodawać je do własnego kodu.

 Fragment kodu jest fragmentem kodu lub innym tekstem, który można dołączyć do pliku. Aby wyświetlić wszystkie fragmenty kodu, które zostały zarejestrowane dla określonych języków programowania, w menu **Narzędzia** kliknij polecenie **Menedżer fragmentów kodu**. Aby wstawić fragment kodu do pliku, kliknij prawym przyciskiem myszy w miejscu, w którym chcesz umieścić fragment kodu, kliknij polecenie Wstaw fragment kodu lub **Otocz za pomocą**, Znajdź odpowiedni fragment kodu, a następnie kliknij go dwukrotnie. Naciśnij klawisz **Tab** lub **SHIFT** +  , aby zmodyfikować odpowiednie fragmenty fragmentu kodu, a następnie naciśnij klawisz **Enter** lub **ESC** , aby je zaakceptować. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](../ide/code-snippets.md).

 Fragment kodu jest zawarty w pliku XML, który ma rozszerzenie nazwy pliku. fragment *. Fragment kodu może zawierać pola, które są wyróżnione po wstawieniu wstawki, aby użytkownik mógł je znaleźć i zmienić. Plik wstawki zawiera również informacje dotyczące **Menedżera fragmentów kodu** , aby można było wyświetlić nazwę fragmentu w prawidłowej kategorii. Aby uzyskać więcej informacji na temat schematu fragmentu kodu, zobacz [odwołania do schematu](../ide/code-snippets-schema-reference.md).

 W tym instruktażu przedstawiono sposób wykonywania następujących zadań:

1. Utwórz i zarejestruj fragmenty kodu dla określonego języka.

2. Dodaj polecenie **Wstaw fragment kodu** do menu skrótów.

3. Zaimplementuj rozszerzenie fragmentu kodu.

   Ten przewodnik jest oparty na [przewodniku: wyświetla uzupełnianie instrukcji](../extensibility/walkthrough-displaying-statement-completion.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dołączana jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-and-register-code-snippets"></a>Tworzenie i rejestrowanie fragmentów kodu
 Zwykle fragmenty kodu są skojarzone z zarejestrowanej usługi językowej. Nie trzeba jednak wdrażać programu <xref:Microsoft.VisualStudio.Package.LanguageService> w celu zarejestrowania fragmentów kodu. Zamiast tego wystarczy określić identyfikator GUID w pliku indeksu fragmentu kodu, a następnie użyć tego samego identyfikatora GUID w elemencie <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> , który zostanie dodany do projektu.

 Poniższe kroki przedstawiają sposób tworzenia fragmentów kodu i kojarzenia ich z określonym identyfikatorem GUID.

1. Utwórz następującą strukturę katalogów:

    **%InstallDir%\TestSnippets\Snippets\1033\\**

    gdzie *% INSTALLDIR%* jest folderem instalacyjnym programu Visual Studio. (Chociaż ta ścieżka jest zwykle używana do instalowania fragmentów kodu, można określić dowolną ścieżkę).

2. W folderze \ 1033 \ Utwórz plik *. XML* i nadaj mu nazwę **TestSnippets.xml**. (Chociaż ta nazwa jest zwykle używana w pliku indeksu fragmentu kodu, można określić dowolną nazwę, o ile ma rozszerzenie nazwy pliku *. XML* ). Dodaj następujący tekst, a następnie usuń zastępczy identyfikator GUID i Dodaj własny.

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

### <a name="to-register-code-snippets-for-a-specific-guid"></a>Aby zarejestrować fragmenty kodu dla określonego identyfikatora GUID

1. Otwórz projekt **CompletionTest** . Aby uzyskać informacje o sposobach tworzenia tego projektu, zobacz [Przewodnik: Kończenie instrukcji Display](../extensibility/walkthrough-displaying-statement-completion.md).

2. W projekcie Dodaj odwołania do następujących zestawów:

    - Microsoft. VisualStudio. TextManager. Interop

    - Microsoft. VisualStudio. TextManager. Interop. 8.0

    - Microsoft. MSXML

3. W projekcie Otwórz plik **source. Extension. vsixmanifest** .

4. Upewnij się, że karta **zasoby** zawiera typ zawartości **pakietu VSPackage** i że **projekt** jest ustawiony na nazwę projektu.

5. Wybierz projekt CompletionTest, a następnie w okno Właściwości Set **Generate pkgdef File** **.** Zapisz projekt.

6. Dodaj klasę statyczną `SnippetUtilities` do projektu.

     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]

7. W klasie SnippetUtilities zdefiniuj identyfikator GUID i nadaj mu wartość użytą w pliku *SnippetsIndex.xml* .

     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]

8. Dodaj <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> do `TestCompletionHandler` klasy. Ten atrybut można dodać do dowolnej klasy publicznej lub wewnętrznej (niestatycznej) w projekcie. (Może być konieczne dodanie `using` dyrektywy do przestrzeni nazw Microsoft. VisualStudio. Shell).

     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]

9. Skompiluj i Uruchom projekt. W eksperymentalnym wystąpieniu programu Visual Studio, które zaczyna się, gdy projekt jest uruchomiony, ten fragment kodu, który właśnie zarejestrowałeś, powinien zostać wyświetlony w **Menedżerze fragmentów kodów** w języku **TestSnippets** .

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>Dodaj polecenie Wstaw fragment kodu do menu skrótów
 Polecenie **Wstaw fragment kodu** nie jest zawarte w menu skrótów dla pliku tekstowego. W związku z tym należy włączyć polecenie.

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Aby dodać polecenie Wstaw wstawki do menu skrótów

1. Otwórz `TestCompletionCommandHandler` plik klasy.

     Ponieważ ta klasa implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , można aktywować polecenie **Wstaw fragment kodu** w <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodzie. Przed włączeniem polecenia Sprawdź, czy ta metoda nie jest wywoływana wewnątrz funkcji automatyzacji, ponieważ po kliknięciu polecenia **Wstaw fragment** kodu zostanie wyświetlony selektor fragmentu interfejsu użytkownika (UI).

     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]

2. Skompiluj i Uruchom projekt. W eksperymentalnym wystąpieniu Otwórz plik, który ma rozszerzenie nazwy pliku *. zzz* , a następnie kliknij prawym przyciskiem myszy w dowolnym miejscu. Polecenie **Wstaw fragment kodu** powinno pojawić się w menu skrótów.

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>Implementuj rozszerzanie fragmentu kodu w interfejsie użytkownika selektora fragmentów kodu
 W tej sekcji pokazano, jak zaimplementować rozszerzenie fragmentu kodu, tak aby interfejs użytkownika selektora fragmentów był wyświetlany po kliknięciu przycisku **Wstaw fragment** w menu skrótów. Fragment kodu jest również rozszerzany, gdy użytkownik wpisze skrót do fragmentu kodu, a następnie naciśnie klawisz **Tab**.

 Aby wyświetlić interfejs użytkownika selektora fragmentów i włączyć funkcję nawigacji i zatwierdzania fragmentów kodu po wstawieniu, użyj <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody. Samo wstawienie jest obsługiwane przez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> metodę.

 Implementacja rozszerzenia fragmentu kodu używa starszych <xref:Microsoft.VisualStudio.TextManager.Interop> interfejsów. W przypadku tłumaczenia z bieżących klas edytora do starszego kodu, należy pamiętać, że starsze interfejsy używają kombinacji numerów wierszy i numerów kolumn do określania lokalizacji w buforze tekstowym, ale bieżące klasy używają jednego indeksu. W związku z tym, jeśli bufor ma trzy wiersze, z których każdy ma 10 znaków (plus znak nowego wiersza, który liczy jako jeden znak), czwarty znak w trzecim wierszu znajduje się na pozycji 27 bieżącej implementacji, ale jest w wierszu 2, pozycja 3 w starej implementacji.

#### <a name="to-implement-snippet-expansion"></a>Aby zaimplementować rozszerzenie fragmentu kodu

1. Do pliku, który zawiera `TestCompletionCommandHandler` klasę, Dodaj następujące `using` dyrektywy.

     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]

2. Ustaw `TestCompletionCommandHandler` klasę jako implementującą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interfejs.

     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]

3. W `TestCompletionCommandHandlerProvider` klasie zaimportuj <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> .

     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]

4. Dodaj pola prywatne dla interfejsów rozszerzających kod i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .

     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]

5. W konstruktorze `TestCompletionCommandHandler` klasy ustaw następujące pola.

     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]

6. Aby wyświetlić selektor wstawki, gdy użytkownik kliknie polecenie **Wstaw fragment** kodu, Dodaj następujący kod do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody. (Aby to wyjaśnienie było bardziej czytelne, `Exec()` kod używany do uzupełniania instrukcji nie jest wyświetlany; zamiast tego, bloki kodu są dodawane do istniejącej metody). Dodaj następujący blok kodu po kodzie, który sprawdza znak.

     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]

7. Jeśli fragment kodu zawiera pola, które mogą być przechodzenie, sesja rozszerzania jest otwarta do momentu, gdy rozszerzanie zostanie jawnie zaakceptowane; Jeśli fragment kodu nie zawiera żadnych pól, sesja jest zamknięta i jest zwracana `null` przez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> metodę. W tej <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodzie, po kodzie interfejsu użytkownika selektora fragmentów, który został dodany w poprzednim kroku, Dodaj następujący kod, aby obsłużyć nawigację fragmentu (gdy użytkownik naciśnie klawisz **Tab** lub **SHIFT** +  po wstawieniu fragmentu kodu).

     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]

8. Aby wstawić fragment kodu, gdy użytkownik wpisze odpowiedni skrót, a następnie naciśnij klawisz **Tab**, Dodaj kod do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody. Metoda prywatna, która wstawia fragment kodu, zostanie wyświetlona w późniejszym kroku. Dodaj następujący kod po kodzie nawigacji, który został dodany w poprzednim kroku.

     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]

9. Zaimplementuj metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interfejsu. W tej implementacji jedyną metodą zainteresowania są <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> . Pozostałe metody powinny po prostu zwrócić <xref:Microsoft.VisualStudio.VSConstants.S_OK> .

     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]

10. Zaimplementuj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> metodę. Metoda pomocnika, która wstawia rozszerzenia, jest omówiona w późniejszym kroku. <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>Zawiera informacje o wierszu i kolumnie, które można uzyskać od <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .

     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]

11. Poniższa metoda prywatna wstawia fragment kodu na podstawie skrótu lub tytułu i ścieżki. Następnie wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> metodę za pomocą fragmentu kodu.

     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]

## <a name="build-and-test-code-snippet-expansion"></a>Kompiluj i Testuj rozszerzanie fragmentu kodu
 Możesz sprawdzić, czy rozszerzenie fragmentu działa w projekcie.

1. Skompiluj rozwiązanie. Po uruchomieniu tego projektu w debugerze uruchomione jest drugie wystąpienie programu Visual Studio.

2. Otwórz plik tekstowy i wpisz tekst.

3. Kliknij prawym przyciskiem myszy w tekście, a następnie kliknij **Wstaw fragment kodu**.

4. Interfejs użytkownika selektora fragmentów powinien pojawić się z wyskakującym menu zawierającym **pola zastępujące testy**. Kliknij dwukrotnie wyskakujące okienko.

     Należy wstawić poniższy fragment kodu.

    ```
    MessageBox.Show("first");
    MessageBox.Show("second");
    ```

     Nie naciskaj klawisza **Enter** ani **ESC**.

5. Naciśnij klawisz **Tab** i **SHIFT** + **,** aby przełączać się między elementami "First" i "Second".

6. Zaakceptuj Wstawianie, naciskając klawisz **Enter** lub **ESC**.

7. W innej części tekstu wpisz "test", a następnie naciśnij klawisz **Tab**. Ponieważ "test" jest skrótem fragmentu kodu, fragment powinien zostać wstawiony ponownie.

## <a name="next-steps"></a>Następne kroki
