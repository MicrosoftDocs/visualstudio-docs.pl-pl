---
title: Utwórz niestandardowy Edytor treści HTTP dla Edytor internetowego testu wydajnościowego
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, custom HTTP body editor
ms.assetid: a0b2d8ff-3e2a-487e-9172-90047174f336
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 02faf2a6c495d7fd5566c8f4291ecaad20ef5eb7
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288147"
---
# <a name="how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor"></a>Instrukcje: Tworzenie niestandardowego edytora treści HTTP dla Edytor internetowego testu wydajnościowego

Można utworzyć niestandardowy Edytor zawartości, który pozwala edytować treść ciągu lub zawartość binarną żądania usługi sieci Web, np. SOAP, REST, asmx, WCF, RIA i innych typów żądań usługi sieci Web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Można zaimplementować następujące rodzaje edytorów:

- **Edytor zawartości ciągów** Jest to implementowane przy użyciu <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> interfejsu.

- **Edytor zawartości binarnej** Jest to implementowane przy użyciu <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> interfejsu.

Te interfejsy są zawarte w <xref:Microsoft.VisualStudio.TestTools.WebTesting> przestrzeni nazw.

## <a name="create-a-windows-control-library-project"></a>Tworzenie projektu biblioteki formantów systemu Windows

1. W programie Visual Studio Utwórz nowy projekt **biblioteki formantów Windows Forms** . Nazwij projekt **MessageEditors**.

   Projekt jest dodawany do nowego rozwiązania, a <xref:System.Windows.Forms.UserControl> nazwana *UserControl1.cs* jest wyświetlana w projektancie.

1. Z **przybornika**w kategorii **Formanty standardowe** przeciągnij a na <xref:System.Windows.Forms.RichTextBox> powierzchnię UserControl1.

1. Wybierz symbol tagu akcji ( ![ symbol tagu inteligentnego ](../test/media/vs_winformsmttagglyph.gif) ) w prawym górnym rogu <xref:System.Windows.Forms.RichTextBox> kontrolki, a następnie wybierz i **Zadokuj w kontenerze nadrzędnym**.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt Biblioteka Windows Forms i wybierz polecenie **Właściwości**.

1. W oknie **Właściwości**wybierz kartę **aplikacja** .

1. Z listy rozwijanej **platforma docelowa** wybierz pozycję .NET Framework 4 (lub nowszy).

1. Zostanie wyświetlone okno dialogowe **zmiana platformy docelowej** .

1. Wybierz opcję **tak**.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **odwołania** i wybierz polecenie **Dodaj odwołanie**.

1. Zostanie wyświetlone okno dialogowe **Dodawanie odwołania** .

1. Wybierz. Kartę **net** , przewiń w dół i wybierz pozycję **Microsoft. VisualStudio. QualityTools. WebTestFramework** , a następnie wybierz **przycisk OK**.

1. Jeśli **Projektant widoków** nie jest wciąż otwarty, w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **UserControl1.cs** , a następnie wybierz polecenie **Projektant widoków**.

1. Na powierzchni projektowej kliknij prawym przyciskiem myszy i wybierz polecenie **Wyświetl kod**.

1. Obowiązkowe Zmień nazwę klasy i konstruktora z UserControl1 na opisową nazwę, na przykład MessageEditorControl:

    > [!NOTE]
    > Przykład używa MessageEditorControl.

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

1. Dodaj następujące właściwości, aby włączyć pobieranie i ustawianie tekstu w RichTextBox1. <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>Interfejs będzie używać EditString i <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> będzie używać EditByteArray:

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

## <a name="add-a-class-to-the-windows-control-library-project"></a>Dodaj klasę do projektu biblioteki formantów systemu Windows

Dodaj klasę do projektu. Zostanie ona użyta do zaimplementowania <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> interfejsów i.

**Przegląd kodu w tej procedurze**

MessageEditorControl <xref:System.Windows.Forms.UserControl> , który został utworzony w poprzedniej procedurze, tworzy wystąpienie jako messageEditorControl:

```csharp
private MessageEditorControl messageEditorControl
```

Wystąpienie messageEditorControl jest hostowane w oknie dialogowym wtyczki, które jest tworzone przez <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.CreateEditor*> metodę. Ponadto messageEditorControl <xref:System.Windows.Forms.RichTextBox> jest wypełniany zawartością w <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> . Jednak nie można utworzyć wtyczki, chyba że <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> zwróci wartość `true` . W przypadku tego edytora <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> zwraca wartość `true` , jeśli w elemencie <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> zawiera "XML".

Gdy edytujesz treść ciągu, a użytkownik kliknie przycisk **OK** w oknie dialogowym wtyczki, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.GetNewValue*> jest wywoływana w celu uzyskania edytowanego tekstu jako ciągu i zaktualizowania **treści ciągu** w żądaniu w edytorze wydajności testów sieci Web.

### <a name="create-a-class-and-implement-the-istringhttpbodyeditorplugin-interface"></a>Tworzenie klasy i implementowanie interfejsu IStringHttpBodyEditorPlugin

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt biblioteka formantów Windows Forms i wybierz polecenie **Dodaj nowy element**.

   Zostanie wyświetlone okno dialogowe **Dodaj nowy element**.

2. Wybierz **klasę**.

3. W polu tekstowym **Nazwa** wpisz nazwę zrozumiałą dla klasy, na przykład `MessageEditorPlugins` .

4. Wybierz pozycję **Dodaj**.

   Class1 jest dodawany do projektu i prezentowany w edytorze kodu.

5. W edytorze kodu Dodaj następującą `using` instrukcję:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    ```

6. Wklej następujący kod w celu zaimplementowania interfejsu:

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

## <a name="add-a-ibinaryhttpbodyeditorplugin-to-the-class"></a>Dodawanie IBinaryHttpBodyEditorPlugin do klasy

Zaimplementuj interfejs <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>.

**Przegląd kodu w tej procedurze**

Implementacja kodu dla <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> interfejsu jest podobna do <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> omówionej w poprzedniej procedurze. Jednak wersja binarna używa tablicy bajtów do obsługi danych binarnych zamiast ciągu.

MessageEditorControl <xref:System.Windows.Forms.UserControl> utworzone w pierwszej procedurze jest tworzone jako messageEditorControl:

```csharp
private MessageEditorControl messageEditorControl
```

Wystąpienie messageEditorControl jest hostowane w oknie dialogowym wtyczki, które jest tworzone przez <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.CreateEditor*> metodę. Ponadto messageEditorControl <xref:System.Windows.Forms.RichTextBox> jest wypełniany zawartością w <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> . Jednak nie można utworzyć wtyczki, chyba że <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> zwróci wartość `true` . W przypadku tego edytora <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> zwraca wartość, `true` Jeśli w elemencie <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> zawiera wartość "msbin1".

Gdy edytujesz treść ciągu, a użytkownik kliknie przycisk **OK** w oknie dialogowym wtyczki, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.GetNewValue*> jest wywoływana w celu uzyskania edytowanego tekstu jako ciągu i aktualizacji **BinaryHttpBody. Data** w żądaniu w edytorze wydajności testów sieci Web.

### <a name="to-add-the-ibinaryhttpbodyeditorplugin-to-the-class"></a>Aby dodać IBinaryHttpBodyEditorPlugin do klasy

- Zapisz lub Skopiuj następujący kod w ramach klasy XmlMessageEditor, która została dodana w poprzedniej procedurze, aby utworzyć wystąpienie klasy Msbin1MessageEditor z <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> interfejsu i zaimplementować wymagane metody:

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

## <a name="build-and-deploy-the-plug-ins"></a>Kompilowanie i wdrażanie wtyczek

1. W menu **kompilacja** wybierz polecenie **Kompiluj \<Windows Form Control Library project name> **.

2. Zamknij wszystkie wystąpienia programu Visual Studio.

   > [!NOTE]
   > Po zamknięciu programu Visual Studio upewnij się, że plik *dll* nie jest zablokowany przed próbą skopiowania.

3. Skopiuj otrzymany plik *dll* z folderu *bin\Debug* projektu (na przykład *MessageEditors.dll*) do *%ProgramFiles%\Microsoft Visual Studio\2017 \\ \<edition> \Common7\IDE\PrivateAssemblies\WebTestPlugins*.

4. Otwórz program Visual Studio.

   *Plik. dll* jest teraz zarejestrowany w programie Visual Studio.

## <a name="verify-the-plug-ins-using-a-web-performance-test"></a>Weryfikowanie wtyczek przy użyciu testu wydajności sieci Web

1. Utwórz projekt testowy.

2. Utwórz test wydajności sieci Web i wprowadź adres URL w przeglądarce do usługi sieci Web.

3. Po zakończeniu nagrywania w Edytor internetowego testu wydajnościowego rozwiń żądanie usługi sieci Web i wybierz **treść ciągu** lub **binarną treść**.

4. W oknie **Właściwości** wybierz opcję treść ciągu lub binarny, a następnie wybierz wielokropek **(...)**.

   Zostanie wyświetlone okno dialogowe **Edytowanie danych treści http** .

5. Teraz można edytować dane i wybrać **przycisk OK**. Powoduje to wywołanie odpowiedniej metody GetNewValue w celu zaktualizowania zawartości w <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> .

## <a name="compile-the-code"></a>Kompiluj kod

Sprawdź, czy platforma domowa dla projektu biblioteki formantów systemu Windows to .NET Framework 4,5. Domyślnie projekty biblioteki formantów systemu Windows są przeznaczone dla platformy klienta .NET Framework 4,5, która nie zezwala na uwzględnienie odwołania Microsoft. VisualStudio. QualityTools. WebTestFramework.

Aby uzyskać więcej informacji, zobacz [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md).

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.RichTextBox>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążeniowych](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Instrukcje: tworzenie wtyczki na poziomie żądania](../test/how-to-create-a-request-level-plug-in.md)
- [Kod reguły wyodrębniania niestandardowego dla testu wydajności sieci Web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kod reguły niestandardowego sprawdzania poprawności dla testu wydajności sieci Web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Instrukcje: tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md)
- [Generowanie i uruchamianie kodowanego testu wydajności sieci Web](../test/generate-and-run-a-coded-web-performance-test.md)
- [Instrukcje: Tworzenie dodatku Visual Studio dla przeglądarki Wyniki testów wydajności sieci Web](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)
