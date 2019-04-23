---
title: 'Przewodnik: Implementowanie fragmentów kodu | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ae22475fa488d93ac4660fdc0cf567f50b32029
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052119"
---
# <a name="walkthrough-implement-code-snippets"></a>Przewodnik: Implementowanie fragmentów kodu
Można tworzyć fragmenty kodu i dołączać do rozszerzenia edytora, tak aby użytkownicy rozszerzenia można dodać je do swój własny kod.

 Fragment kodu jest fragmentem kodu lub inny tekst, który może być zawarte w pliku. Aby wyświetlić wszystkie fragmenty kodu, które zostały zarejestrowane dla określonych języków programowania, na **narzędzia** menu, kliknij przycisk **Menedżera fragmentów kodu**. Aby wstawić framgent kodu w pliku, kliknij prawym przyciskiem myszy, którego ten fragment kodu kliknij przycisk Wstaw fragment kodu lub **Otocz**, fragment, chcesz, aby zlokalizować i kliknij ją dwukrotnie. Naciśnij klawisz **kartę** lub **Shift**+**kartę** zmodyfikuj odpowiednie części fragmentu kodu, a następnie naciśnij klawisz **Enter** lub **Esc** go zaakceptować. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](../ide/code-snippets.md).

 Fragment kodu znajduje się w pliku XML, który ma rozszerzenie nazwy pliku .snippet *. Fragment może zawierać pola, które są wyróżnione po wstawieniu fragmentu, tak aby użytkownik może znaleźć i zmień je. Plik fragmentu również informacje dotyczące **Menedżera fragmentów kodu** tak, aby go wyświetlić nazwy fragmentu kodu w odpowiedniej kategorii. Aby uzyskać informacji na temat schematu fragmentu kodu, zobacz [odwołanie do schematu fragmentów kodu](../ide/code-snippets-schema-reference.md).

 Ten przewodnik omawia sposób wykonywania tych zadań:

1. Utwórz i zarejestruj fragmentów kodu dla określonego języka.

2. Dodaj **Wstaw fragment kodu** polecenia do menu skrótów.

3. Implementowanie rozszerzenia fragmentu kodu.

   Ten przewodnik jest oparty na [instruktażu: Wyświetlanie uzupełniania instrukcji](../extensibility/walkthrough-displaying-statement-completion.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie instaluj programu Visual Studio SDK z Centrum pobierania. Został on uwzględniony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-and-register-code-snippets"></a>Utwórz i zarejestruj fragmentów kodu
 Zazwyczaj fragmenty kodu są skojarzone z usługą language zarejestrowane. Jednak nie trzeba implementować <xref:Microsoft.VisualStudio.Package.LanguageService> zarejestrować fragmentów kodu. Zamiast tego po prostu określić identyfikator GUID w pliku indeksu fragmentu kodu, a następnie użyj tego samego identyfikatora GUID w <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> dodanego do projektu.

 Poniższe kroki pokazują, jak utworzyć fragmenty kodu i skojarzyć je z określonym identyfikatorem GUID.

1. Utwórz następującą strukturę katalogów:

    **%InstallDir%\TestSnippets\Snippets\1033\\**

    gdzie *InstallDir %* jest folder instalacji programu Visual Studio. (Mimo że ta ścieżka jest zazwyczaj używana do zainstalowania fragmenty kodu, można określić dowolną ścieżkę).

2. W folderze \1033\ Utwórz *.xml* plik i nadaj mu nazwę **TestSnippets.xml**. (Mimo że ta nazwa jest zazwyczaj używana do pliku indeksu fragmentu kodu, można określić dowolną nazwę, tak długo, jak przedstawiono w nim *.xml* rozszerzenie nazwy pliku.) Dodaj następujący tekst, a następnie usuń symbol zastępczy identyfikator GUID i dodać własne.

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

3. Utwórz plik w folderze fragmentów kodu, nadaj jej nazwę **test**`.snippet`, a następnie dodaj następujący tekst:

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

   Poniższe kroki pokazują jak zarejestrować fragmentów kodu.

### <a name="to-register-code-snippets-for-a-specific-guid"></a>Aby zarejestrować fragmentów kodu dla określonego identyfikatora GUID

1. Otwórz **CompletionTest** projektu. Aby uzyskać informacje dotyczące sposobu tworzenia tego projektu, zobacz [instruktażu: Wyświetlanie uzupełniania instrukcji](../extensibility/walkthrough-displaying-statement-completion.md).

2. W projekcie należy dodać odwołania do następujących zestawów:

    - Microsoft.VisualStudio.TextManager.Interop

    - Microsoft.VisualStudio.TextManager.Interop.8.0

    - microsoft.msxml

3. W projekcie, otwórz **source.extension.vsixmanifest** pliku.

4. Upewnij się, że **zasoby** karta zawiera **pakietu VsPackage** zawartości typu i który **projektu** jest ustawiona na nazwę projektu.

5. Wybierz projekt CompletionTest i w oknie właściwości ustaw **Generowanie pliku Pkgdef** do **true**. Zapisz projekt.

6. Dodaj statyczną `SnippetUtilities` klasy do projektu.

     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]

7. W klasie SnippetUtilities zdefiniować identyfikator GUID i nadaj mu wartość, która została użyta w *SnippetsIndex.xml* pliku.

     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]

8. Dodaj <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> do `TestCompletionHandler` klasy. Ten atrybut można dodać do każdej klasy publiczne lub wewnętrzny (niestatycznych) w projekcie. (Być może trzeba dodać `using` instrukcji dla przestrzeni nazw Microsoft.VisualStudio.Shell.)

     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]

9. Skompiluj i uruchom projekt. W doświadczalnym wystąpieniu programu Visual Studio, który rozpoczyna się podczas uruchamiania projektu, fragment kodu, które właśnie zostało zarejestrowane, powinny być wyświetlane w **Menedżera wstawek kodu** w obszarze **TestSnippets** języka.

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>Dodaj polecenie Wstaw fragment kodu do menu skrótów
 **Wstaw fragment kodu** polecenia nie jest uwzględniony w menu skrótów dla pliku tekstowego. W związku z tym należy włączyć polecenia.

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Aby dodać polecenie Wstaw fragment kodu do menu skrótów

1. Otwórz `TestCompletionCommandHandler` pliku klasy.

     Ponieważ ta klasa implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, możesz aktywować **Wstaw fragment kodu** polecenia w pliku <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody. Przed włączeniem polecenia Sprawdź, czy ta metoda nie jest wywoływana wewnątrz funkcji automatyzacji, ponieważ gdy **Wstaw fragment kodu** kliknięciu polecenia, wyświetla się interfejsie użytkownika (UI) selektor fragmentu kodu.

     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]

2. Skompiluj i uruchom projekt. W doświadczalnym wystąpieniu, należy otworzyć plik, który ma *.zzz* rozszerzenie nazwy pliku, a następnie kliknij prawym przyciskiem myszy w nim. **Wstaw fragment kodu** polecenie powinno pojawić się w menu skrótów.

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>Implementowanie rozszerzenia fragmentu kodu w Interfejsie użytkownika selektora fragmentu kodu
 W tej sekcji przedstawia sposób implementowania rozszerzenie fragment kodu, tak, aby selektor fragmentu kodu interfejsu użytkownika jest wyświetlany, gdy **Wstaw fragment kodu** kliknięciu menu skrótów. Fragment kodu również jest rozszerzona, gdy użytkownik wpisze skrótów fragmentu kodu, a następnie naciska klawisz **kartę**.

 Aby wyświetlić selektor fragmentu kodu interfejsu użytkownika i włączyć nawigacji i akceptacji po wstawiania fragmentu kodu, należy użyć <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody. Wstawianie, sama jest obsługiwana przez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> metody.

 Implementacja rozszerzenie fragment kodu używa starszej wersji <xref:Microsoft.VisualStudio.TextManager.Interop> interfejsów. Podczas tłumaczenia z bieżącej klasy edytora do starszego kodu, należy pamiętać, że interfejsy starszej wersji użyć kombinacji numery wierszy i kolumn liczb, aby określić lokalizacje w buforze tekstu, lecz bieżącej klasy używa jednego indeksu. W związku z tym jeśli bufor składa się z trzema wierszami, z których każdy ma 10 znaków (plus nowego wiersza, który jest liczona jako jeden znak), znaku czwartego w trzecim wierszu znajduje się na pozycji 27 w bieżącej implementacji, ale jest w wierszu 2, umieść 3 w starym wykonywaniu.

#### <a name="to-implement-snippet-expansion"></a>Aby zaimplementować rozszerzenia fragmentu kodu

1. Do pliku, który zawiera `TestCompletionCommandHandler` klasy, Dodaj następujący kod `using` instrukcji.

     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]

2. Wprowadź `TestCompletionCommandHandler` implementacji klasy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interfejsu.

     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]

3. W `TestCompletionCommandHandlerProvider` klasy, import <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>.

     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]

4. Dodaj pola prywatne dla interfejsów rozszerzenia kodu i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.

     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]

5. W Konstruktorze typu `TestCompletionCommandHandler` klasy, ustaw następujące pola.

     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]

6. Aby wyświetlić selektor fragmentu kodu, gdy użytkownik kliknie **Wstaw fragment kodu** polecenia, należy dodać następujący kod do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody. (Się bardziej czytelny, to wyjaśnienie `Exec()`nie jest wyświetlany kod, który jest używany do uzupełniania; zamiast tego bloki kodu są dodawane do istniejącej metody.) Dodaj następujący blok kodu po kodzie, który sprawdza, czy znak.

     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]

7. Jeśli fragment kodu zawiera pola, które można go znaleźć, sesja rozszerzenia pozostaje otwarte do momentu rozszerzenie jawnie zaakceptowania; Jeśli fragment kodu nie ma pól, sesja jest zamknięta i jest zwracana jako `null` przez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> metody. W <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody po selektor fragmentu kodu interfejsu użytkownika, który zostało dodane w poprzednim kroku, Dodaj następujący kod do obsługi nawigacji do fragmentu kodu (gdy użytkownik naciśnie **kartę** lub **Shift** + **Kartę** po wstawieniu fragmentu kodu).

     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]

8. Aby wstawić fragment kodu, jeśli użytkownik wpisze odpowiedniego skrótu, a następnie naciska klawisz **kartę**, Dodaj kod, aby <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody. Metoda prywatna, który wstawia fragment kodu będą wyświetlane w kolejnym kroku. Dodaj następujący kod po kodzie nawigacji, dodanej w poprzednim kroku.

     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]

9. Implementuje metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interfejsu. W tej implementacji, są jedyne metody zainteresowania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Inne metody tylko powinna zwrócić <xref:Microsoft.VisualStudio.VSConstants.S_OK>.

     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]

10. Implementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> metody. Metody pomocnika, która faktycznie wstawia rozszerzenia są omówione w dalszej części. <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> Informacje wiersza i kolumny, którą można pobrać z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.

     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]

11. Następującą prywatną metodę wstawia fragment kodu, albo na podstawie skrótu lub tytuł i ścieżkę. Następnie wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> metoda fragmentem kodu.

     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]

## <a name="build-and-test-code-snippet-expansion"></a>Tworzenie i testowanie rozszerzenia fragmentu kodu
 Możesz sprawdzić, czy rozszerzenie fragment działa w projekcie.

1. Skompiluj rozwiązanie. Po uruchomieniu tego projektu w debugerze, drugie wystąpienie programu Visual Studio został uruchomiony.

2. Otwórz plik tekstowy i wpisz jakiś tekst.

3. Kliknij prawym przyciskiem myszy gdzieś w tekście, a następnie kliknij przycisk **Wstaw fragment kodu**.

4. Selektor fragmentu kodu interfejsu użytkownika powinno zostać wyświetlone okno podręczne, które mówi **pola zastąpienie testowe**. Kliknij dwukrotnie oknie podręcznym.

     Poniższy fragment kodu można wstawić.

    ```
    MessageBox.Show("first");
    MessageBox.Show("second");
    ```

     Nie naciśnij **Enter** lub **Esc**.

5. Naciśnij klawisz **kartę** i **Shift**+**kartę** można przełączać się między "first" i "drugi".

6. Zaakceptuj wstawiania, naciskając klawisz albo **Enter** lub **Esc**.

7. W różnych części tekstu, wpisz "test", a następnie naciśnij klawisz **kartę**. Ponieważ "test" skrótów fragmentu kodu, fragment kodu powinien zostać wstawiony ponownie.

## <a name="next-steps"></a>Następne kroki