---
title: Tworzenie niestandardowego edytora treści HTTP dla Edytora testów wydajności sieci Web
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, custom HTTP body editor
ms.assetid: a0b2d8ff-3e2a-487e-9172-90047174f336
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: efc9a959fa02b62583e7bf366e8c580b2876a4a1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589204"
---
# <a name="how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor"></a>Jak: Tworzenie niestandardowego edytora treści HTTP dla Edytora testów wydajności sieci Web

Można utworzyć niestandardowy edytor zawartości, który umożliwia edycję zawartości treści ciągu lub zawartości treści binarnej żądania usługi sieci web, na przykład SOAP, REST, asmx, wcf, RIA i innych typów żądań usługi sieci web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Można zaimplementować następujące rodzaje edytorów:

- **Edytor zawartości ciągów** Jest to realizowane <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> przy użyciu interfejsu.

- **Edytor treści binarnych** Jest to realizowane <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> przy użyciu interfejsu.

Te interfejsy są zawarte <xref:Microsoft.VisualStudio.TestTools.WebTesting> w obszarze nazw.

## <a name="create-a-windows-control-library-project"></a>Tworzenie projektu biblioteki sterowania systemem Windows

1. W programie Visual Studio utwórz nowy projekt **biblioteki kontroli formularzy systemu Windows.** Nazwij projekt **MessageEditors**.

   Projekt zostanie dodany do nowego <xref:System.Windows.Forms.UserControl> rozwiązania i nazwany *UserControl1.cs* jest przedstawiony w Projektancie.

1. Z **przybornika**, w kategorii Typowe <xref:System.Windows.Forms.RichTextBox> **formanty,** przeciągnij na powierzchni UserControl1.

1. Wybierz glif znacznika![akcji (Smart](../test/media/vs_winformsmttagglyph.gif)Tag Glyph) w <xref:System.Windows.Forms.RichTextBox> prawym górnym rogu formantu, a następnie wybierz i **Dokuj w kontenerze nadrzędnym**.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt Biblioteki formularzy systemu Windows i wybierz polecenie **Właściwości**.

1. W oknie **Właściwości**wybierz kartę **Aplikacja.**

1. Na liście rozwijanej **Struktura docelowa** wybierz .NET Framework 4 (lub nowsze).

1. Zostanie wyświetlone okno dialogowe **Zmiana struktury docelowej.**

1. Wybierz **pozycję Tak**.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł **Odwołania** i wybierz polecenie **Dodaj odwołanie**.

1. Zostanie wyświetlone okno dialogowe **Dodawanie odwołania.**

1. Wybierz opcję . **NET,** przewiń w dół i wybierz pozycję **Microsoft.VisualStudio.QualityTools.WebTestFramework,** a następnie wybierz przycisk **OK**.

1. Jeśli **projektant widoku** nie jest nadal otwarty, w **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **UserControl1.cs** a następnie wybierz polecenie **Wyświetl projektanta**.

1. Na powierzchni projektowej kliknij prawym przyciskiem myszy i wybierz polecenie **Wyświetl kod**.

1. (Opcjonalnie) Zmień nazwę klasy i konstruktora z UserControl1 na znaczącą nazwę, na przykład MessageEditorControl:

    > [!NOTE]
    > W przykładzie użyto MessageEditorControl.

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

1. Dodaj następujące właściwości, aby umożliwić uzyskiwanie i ustawianie tekstu w richtextbox1. Interfejs <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> będzie używać EditString <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> i będzie używać EditByteArray:

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

## <a name="add-a-class-to-the-windows-control-library-project"></a>Dodawanie klasy do projektu Biblioteki sterowania systemu Windows

Dodaj klasę do projektu. Będzie on używany do <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> implementacji i interfejsów.

**Omówienie kodu w tej procedurze**

MessageEditorControl, <xref:System.Windows.Forms.UserControl> który został utworzony w poprzedniej procedurze jest tworzone jako messageEditorControl:

```csharp
private MessageEditorControl messageEditorControl
```

Wystąpienie messageEditorControl jest hostowane w oknie dialogowym <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.CreateEditor*> dodatku plug-in, które jest tworzone przez metodę. Ponadto messageEditorControl jest wypełniona <xref:System.Windows.Forms.RichTextBox> zawartością w <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>. Jednak tworzenie wtyczki nie może wystąpić, chyba że <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> zwraca `true`. W przypadku tego edytora zwraca, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> `true` jeśli <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> w zawiera "xml".

Po zakończeniu edycji treści ciągu i kliknięciu **przycisku OK** w <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.GetNewValue*> oknie dialogowym dodatku plug-in, jest wywoływana, aby uzyskać edytowany tekst jako ciąg i zaktualizować **treść ciągu** w żądaniu w Edytorze wydajności testów sieci Web.

### <a name="create-a-class-and-implement-the-istringhttpbodyeditorplugin-interface"></a>Tworzenie klasy i implementowanie interfejsu IStringHttpBodyEditorPlugin

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt Biblioteki sterowania formularzami systemu Windows i wybierz polecenie **Dodaj nowy element**.

   Zostanie wyświetlone okno dialogowe **Dodaj nowy element**.

2. Wybierz **klasę**.

3. W polu tekstowym **Nazwa** wpisz na przykład opisową `MessageEditorPlugins`nazwę klasy .

4. Wybierz **pozycję Dodaj**.

   Klasa1 jest dodawany do projektu i prezentowane w Edytorze kodu.

5. W edytorze kodu dodaj `using` następującą instrukcję:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    ```

6. Wklej w następującym kodzie, aby zaimplementować interfejs:

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

## <a name="add-a-ibinaryhttpbodyeditorplugin-to-the-class"></a>Dodawanie do klasy elementu IBinaryHttpBodyEditorPlugin

Zaimplementuj interfejs <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>.

**Omówienie kodu w tej procedurze**

Implementacja kodu <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> dla interfejsu jest <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> podobna do opisanej w poprzedniej procedurze. Jednak wersja binarna używa tablicy bajtów do obsługi danych binarnych zamiast ciągu.

MessageEditorControl <xref:System.Windows.Forms.UserControl> utworzony w pierwszej procedurze jest tworzona jako messageEditorControl:

```csharp
private MessageEditorControl messageEditorControl
```

Wystąpienie messageEditorControl jest hostowane w oknie dialogowym <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.CreateEditor*> dodatku plug-in, które jest tworzone przez metodę. Ponadto messageEditorControl jest wypełniona <xref:System.Windows.Forms.RichTextBox> zawartością w <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>. Jednak tworzenie wtyczki nie może wystąpić, chyba że <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> zwraca `true`. W przypadku tego edytora zwraca, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> `true` jeśli <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> w zawiera "msbin1".

Po zakończeniu edycji treści ciągu i kliknięciu przycisku **OK** w <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.GetNewValue*> oknie dialogowym wtyczki, jest wywoływana, aby uzyskać edytowany tekst jako ciąg i zaktualizować **BinaryHttpBody.Data** w żądaniu w Edytorze wydajności testów sieci Web.

### <a name="to-add-the-ibinaryhttpbodyeditorplugin-to-the-class"></a>Aby dodać iBinaryHttpBodyEditorPlugin do klasy

- Napisz lub skopiuj następujący kod w ramach klasy XmlMessageEditor dodanej w poprzedniej procedurze <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> w celu wystąpienia klasy Msbin1MessageEditor z interfejsu i zaimplementowania wymaganych metod:

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

## <a name="build-and-deploy-the-plug-ins"></a>Tworzenie i wdrażanie wtyczek

1. W menu **Kompilacja** wybierz polecenie **Tworzenie \<nazwy projektu Biblioteki sterowania formularzami systemu Windows>**.

2. Zamknij wszystkie wystąpienia programu Visual Studio.

   > [!NOTE]
   > Zamknięcie programu Visual Studio upewnia się, że plik *dll* nie jest zablokowany przed próbą jego skopiowania.

3. Skopiuj wynikowy plik *dll* z folderu *bin\debugowania* projektu (na przykład *MessageEditors.dll*) do *%ProgramFiles%\Microsoft Visual Studio\2017\\\<edition>\Common7\IDE\PrivateAssemblies\WebTestPlugins*.

4. Otwórz program Visual Studio.

   Biblioteka *.dll* jest teraz zarejestrowana w programie Visual Studio.

## <a name="verify-the-plug-ins-using-a-web-performance-test"></a>Weryfikowanie wtyczek za pomocą testu wydajności sieci Web

1. Tworzenie projektu testowego.

2. Utwórz test wydajności sieci Web i wprowadź adres URL w przeglądarce do usługi sieci web.

3. Po zakończeniu nagrywania w Edytorze testów wydajności sieci Web rozwiń żądanie dla usługi sieci web i wybierz **treść ciągu** lub **obiekt binarny**.

4. W oknie **Właściwości** wybierz obiekt ciągów lub obiekt binarny i wybierz wielokropek **(...)**.

   Zostanie wyświetlone okno dialogowe **Edytowanie danych treści HTTP.**

5. Teraz możesz edytować dane i wybrać **przycisk OK**. Wywołuje to odpowiednią metodę GetNewValue, aby <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>zaktualizować zawartość w pliku .

## <a name="compile-the-code"></a>Skompiluj kod

Sprawdź, czy docelową strukturą dla projektu biblioteki sterowania systemu Windows jest .NET Framework 4.5. Domyślnie projekty biblioteki sterowania systemu Windows są przeznaczone dla platformy klienta programu .NET Framework 4.5, która nie zezwala na dołączanie odwołania microsoft.VisualStudio.QualityTools.WebTestFramework.

Aby uzyskać więcej informacji, zobacz [stronę aplikacji, projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md).

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.RichTextBox>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążeniowych](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Jak: Tworzenie wtyczki na poziomie żądania](../test/how-to-create-a-request-level-plug-in.md)
- [Kodowania niestandardowej reguły wyodrębniania dla testu wydajności sieci Web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kodowania niestandardowej reguły sprawdzania poprawności dla testu wydajności sieci Web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Jak: Tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md)
- [Generowanie i uruchamianie kodowanego testu wydajności sieci Web](../test/generate-and-run-a-coded-web-performance-test.md)
- [Jak: Tworzenie dodatku programu Visual Studio dla Podglądu wyników testów wydajności sieci Web](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)
