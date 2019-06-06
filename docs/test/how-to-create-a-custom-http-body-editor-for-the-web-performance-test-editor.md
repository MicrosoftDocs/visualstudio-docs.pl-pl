---
title: Utwórz HTTP niestandardowego edytora treści do edytora testów wydajności sieci Web
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, custom HTTP body editor
ms.assetid: a0b2d8ff-3e2a-487e-9172-90047174f336
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 624d06dd44812269bcff1e67cf048fbb077e90ea
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66745825"
---
# <a name="how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor"></a>Instrukcje: Utwórz HTTP niestandardowego edytora treści do edytora testów wydajności sieci Web

Można tworzyć Edytor treści niestandardowych, który umożliwia edytowanie treść ciągu lub dane binarne ciała treści żądania usługi sieci web, na przykład SOAP, REST, asmx, wcf, RIA i inne typy żądań usług sieci web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Można zaimplementować te rodzaje edytorów:

- **Edytor zawartości ciągu** ten sposób jest implementowany przy użyciu <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> interfejsu.

- **Edytor zawartości binarnej** ten sposób jest implementowany przy użyciu <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> interfejsu.

Te interfejsy są zawarte w <xref:Microsoft.VisualStudio.TestTools.WebTesting> przestrzeni nazw.

## <a name="create-a-windows-control-library-project"></a>Utwórz projekt Biblioteka formantów Windows

1. W programie Visual Studio Utwórz nowy **Biblioteka kontrolek formularzy Windows** projektu. Nadaj projektowi nazwę **MessageEditors**.

   Projekt jest dodawany do nowego rozwiązania i <xref:System.Windows.Forms.UserControl> o nazwie *UserControl1.cs* jest przedstawiany w projektancie.

1. Z **przybornika**w obszarze **wspólnych formantów** przeciągnij <xref:System.Windows.Forms.RichTextBox> na powierzchnię obiektu UserControl1.

1. Wybierz symbol tagu akcji (![symbol tagu inteligentnego](../test/media/vs_winformsmttagglyph.gif)) w prawym górnym rogu <xref:System.Windows.Forms.RichTextBox> sterowania, a następnie wybierz i **Zadokuj w kontenerze nadrzędnym**.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt Biblioteka formularzy Windows i wybierz **właściwości**.

1. W **właściwości**, wybierz opcję **aplikacji** kartę.

1. W **platformę docelową** listy rozwijanej, wybierz pozycję .NET Framework 4 (lub nowsza).

1. **Zmiana platformy docelowej** zostanie wyświetlone okno dialogowe.

1. Wybierz **tak**.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** a następnie wybierz węzeł **Dodaj odwołanie**.

1. **Dodaj odwołanie** zostanie wyświetlone okno dialogowe.

1. Wybierz opcję. **NET** karty, przewiń w dół i wybierz **Microsoft.VisualStudio.QualityTools.WebTestFramework** , a następnie wybierz **OK**.

1. Jeśli **Projektant widoków** nie jest wciąż otwarty w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **UserControl1.cs** , a następnie wybierz **Projektant widoków**.

1. Na powierzchni projektowej kliknij prawym przyciskiem myszy i wybierz **Wyświetl kod**.

1. (Opcjonalnie) Zmień nazwę klasy i konstruktora z UserControl1 na nazwę opisową, na przykład MessageEditorControl:

    > [!NOTE]
    > W przykładzie zastosowano MessageEditorControl.

    ```csharp
    namespace MessageEditors
    {
        public partial class MessageEditorControl : UserControl
        {
            public MessageEditorControl()
            {
                InitializeComponent();
            }
        }
    }
    ```

1. Dodaj następujące właściwości, aby umożliwić uzyskanie i ustawienie tekstu w RichTextBox1. <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> Interfejsu będzie używać EditString a <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> będzie używać EditByteArray:

    ```csharp
    public String EditString
    {
       get
       {
           return this.richTextBox1.Text;
       }
       set
       {
           this.richTextBox1.Text = value;
       }
    }

    public byte[] EditByteArray
    {
       get
       {
           return System.Convert.FromBase64String(richTextBox1.Text);
       }
       set
       {
           richTextBox1.Text = System.Convert.ToBase64String(value, 0, value.Length);
       }
    }
    ```

## <a name="add-a-class-to-the-windows-control-library-project"></a>Dodaj klasę do projektu Biblioteka formantów Windows

Dodaj klasę do projektu. Będzie służyć do implementowania <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> i <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> interfejsów.

**Przegląd kodu w tej procedurze**

MessageEditorControl <xref:System.Windows.Forms.UserControl> utworzony w poprzedniej procedurze zostanie uruchomiony jako messageEditorControl:

```csharp
private MessageEditorControl messageEditorControl
```

 Wystąpienie messageEditorControl znajduje się w oknie dialogowym wtyczki, utworzony przez <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.CreateEditor*> metody. Ponadto messageEditorControl <xref:System.Windows.Forms.RichTextBox> jest wypełniana przy użyciu zawartości <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>. Jednak tworzenie wtyczki nie może wystąpić, chyba że <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> zwraca `true`. W przypadku tego edytora <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> zwraca `true` Jeśli <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> w <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> zawiera element "xml".

 Po zakończeniu edycji ciągu i użytkownik klika polecenie **OK** w oknie dialogowym wtyczki, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.GetNewValue*> jest wywoływana w celu uzyskania edytowanego tekstu jako ciągu i aktualizacji **ciąg tekstowy** w żądaniu w sieci Web Edytorze wydajności testów.

### <a name="create-a-class-and-implement-the-istringhttpbodyeditorplugin-interface"></a>Utwórz klasę i zaimplementować interfejsu IStringHttpBodyEditorPlugin

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt Biblioteka kontrolek formularzy Windows i wybierz **Dodaj nowy element**.

   **Dodaj nowy element** zostanie wyświetlone okno dialogowe.

2. Wybierz **klasy**.

3. W **nazwa** tekstu wpisz opisową nazwę dla tej klasy, na przykład `MessageEditorPlugins`.

4. Wybierz **Dodaj**.

   Moduł Class1 jest dodawany do projektu i przedstawiony w edytorze kodu.

5. W edytorze kodu Dodaj następujący kod `using` instrukcji:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    ```

6. Wklej następujący kod, aby zaimplementować interfejs:

    ```csharp
    /// <summary>
    /// Editor for generic text based hierarchical messages such as XML and JSON.
    /// </summary>
    public class XmlMessageEditor : IStringHttpBodyEditorPlugin
    {
        public XmlMessageEditor()
        {
        }

        /// <summary>
        /// Determine if this plugin supports the content type.
        /// </summary>
        /// <param name="contentType">The content type to test.</param>
        /// <returns>Returns true if the plugin supports the specified content type.</returns>
        public bool SupportsContentType(string contentType)
        {
            return contentType.ToLower().Contains("xml");
        }

        /// <summary>
        /// Create a UserControl to edit the specified bytes.
        /// This control will be hosted in the
        /// plugin dialog which provides OK and Cancel buttons.
        /// </summary>
        /// <param name="contentType">The content type of the BinaryHttpBody.</param>
        /// <param name="initialValue">The bytes to edit. The bytes are the payload of a BinaryHttpBody.</param>
        /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
        public object CreateEditor(string contentType, string initialValue)
        {
            messageEditorControl = new MessageEditorControl();
            messageEditorControl.EditString = initialValue;
            return this.messageEditorControl;
        }

        /// <summary>
        /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
        /// </summary>
        public string GetNewValue()
        {
            return messageEditorControl.EditString;
        }

        private MessageEditorControl messageEditorControl;
    }
    ```

## <a name="add-a-ibinaryhttpbodyeditorplugin-to-the-class"></a>Dodaj IBinaryHttpBodyEditorPlugin do klasy

Implementowanie <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> interfejsu.

**Przegląd kodu w tej procedurze**

Implementacja kodu dla <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> interfejs jest podobny do <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> opisane w poprzedniej procedurze. Jednak binarna wersja wykorzystuje tablicę bajtów do obsługi danych binarnych zamiast ciągu.

MessageEditorControl <xref:System.Windows.Forms.UserControl> utworzone w pierwszej procedurze zostanie uruchomiony jako messageEditorControl:

```csharp
private MessageEditorControl messageEditorControl
```

Wystąpienie messageEditorControl znajduje się w oknie dialogowym wtyczki, utworzony przez <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.CreateEditor*> metody. Ponadto messageEditorControl <xref:System.Windows.Forms.RichTextBox> jest wypełniana przy użyciu zawartości <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>. Jednak tworzenie wtyczki nie może wystąpić, chyba że <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> zwraca `true`. W przypadku tego edytora <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> zwraca `true` Jeśli <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> w <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> zawiera "wartość msbin1".

Po zakończeniu edycji ciągu i użytkownik klika polecenie **OK** w oknie dialogowym wtyczki, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.GetNewValue*> jest wywoływana w celu uzyskania edytowanego tekstu jako ciągu i aktualizacji **BinaryHttpBody.Data** w żądaniu w sieci Web edytorze wydajności testów.

### <a name="to-add-the-ibinaryhttpbodyeditorplugin-to-the-class"></a>Aby dodać IBinaryHttpBodyEditorPlugin do klasy

- Zapisz lub skopiuj poniższy kod w klasie XmlMessageEditor dodany w poprzedniej procedurze, aby utworzyć wystąpienie klasy Msbin1MessageEditor z <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> interfejs i wdrożyć wymagane metody:

    ```csharp
    /// <summary>
        /// Editor for MSBin1 content type (WCF messages)
        /// </summary>
        public class Msbin1MessageEditor : IBinaryHttpBodyEditorPlugin
        {
            /// <summary>
            ///
            /// </summary>
            public Msbin1MessageEditor()
            {
            }

            /// <summary>
            /// Determine if this plugin supports a content type.
            /// </summary>
            /// <param name="contentType">The content type to test.</param>
            /// <returns>Returns true if the plugin supports the specified content type.</returns>
            public bool SupportsContentType(string contentType)
            {
                return contentType.ToLower().Contains("msbin1");
            }

            /// <summary>
            /// Create a UserControl to edit the specified bytes. This control will be hosted in the
            /// plugin dialog which provides OK and Cancel buttons.
            /// </summary>
            /// <param name="contentType">The content type of the BinaryHttpBody.</param>
            /// <param name="initialValue">The bytes to edit. The bytes are the payload of a BinaryHttpBody.</param>
            /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
            public object CreateEditor(string contentType, byte[] initialValue)
            {
                messageEditorControl = new MessageEditorControl();
                messageEditorControl.EditByteArray = initialValue;
                return messageEditorControl;
            }

            /// <summary>
            /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
            /// </summary>
            public byte[] GetNewValue()
            {
                return messageEditorControl.EditByteArray;
            }

            private MessageEditorControl messageEditorControl;
            private object originalMessage;
        }
    ```

## <a name="build-and-deploy-the-plug-ins"></a>Tworzenie i wdrażanie dodatków plug-in

1. Na **kompilacji** menu, wybierz **kompilacji \<Nazwa projektu biblioteki formantów Windows >** .

2. Zamknij wszystkie wystąpienia programu Visual Studio.

   > [!NOTE]
   > Zamykanie programu Visual Studio zapewniają, że *.dll* plik nie jest zablokowany, przed podjęciem próby skopiowania go.

3. Skopiuj wynikowy *.dll* plik z projektu *bin\debug* folderu (na przykład *MessageEditors.dll*) do *%ProgramFiles%\Microsoft Visual Studio\2017\\\<edition > \Common7\IDE\PrivateAssemblies\WebTestPlugins*.

4. Otwórz program Visual Studio.

   *.Dll* jest obecnie zarejestrowany za pomocą programu Visual Studio.

## <a name="verify-the-plug-ins-using-a-web-performance-test"></a>Sprawdź wtyczki za pomocą testu wydajności sieci Web

1. Utwórz projekt testu.

2. Utwórz test wydajności sieci web i wprowadź adres URL usługi sieci web w przeglądarce.

3. Po zakończeniu rejestrowania w sieci Web edytorze testów wydajności, rozwiń żądania usługi sieci web i wybierz opcję **ciąg tekstowy** lub **dane binarne ciała**.

4. W **właściwości** okno, wybierz opcję ciąg tekstowy lub dane binarne ciała treści i wybierz przycisk wielokropka **(...)** .

   **Edytowanie danych treści HTTP** zostanie wyświetlone okno dialogowe.

5. Możesz teraz edytować dane i wybrać **OK**. Wywołuje to metodę GetNewValue w celu aktualizacji zawartości w <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>.

## <a name="compile-the-code"></a>Skompilować kod

Sprawdź, czy framework docelowa dla projektu Biblioteka formantów Windows .NET Framework 4.5. Domyślnie projekty biblioteki formantów Windows docelowa Architektura klienta programu .NET Framework 4.5, której nie pozwoli na włączenie odniesienia Microsoft.VisualStudio.QualityTools.WebTestFramework.

Aby uzyskać więcej informacji, zobacz [strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md).

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.RichTextBox>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążenia](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Instrukcje: Tworzenie wtyczki na poziomie żądania](../test/how-to-create-a-request-level-plug-in.md)
- [Kod niestandardowej reguły wyodrębniania dla testów wydajności sieci web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kod niestandardowej reguły walidacji dla testów wydajności sieci web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Instrukcje: Tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md)
- [Generowanie i uruchom kodowany internetowy test wydajnościowy](../test/generate-and-run-a-coded-web-performance-test.md)
- [Instrukcje: Tworzenie dodatku programu Visual Studio dla podglądu wyników testu wydajności sieci Web](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)