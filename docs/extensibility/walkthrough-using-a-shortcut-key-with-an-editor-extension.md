---
title: 'Przewodnik: Korzystanie z klawisza skrótu z rozszerzeniem edytora | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 651598c0dbe746a9a26a6d60ce72b02853f98d47
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697148"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>Instruktaż: używanie klawisza skrótu z rozszerzeniem edytora
Możesz odpowiadać na klawisze skrótów w rozszerzeniu edytora. W poniższym przewodniku pokazano, jak dodać ozdoby widoku do widoku tekstowego za pomocą klawisza skrótu. Ten instruktaż jest oparty na szablonie edytora ozdabień rzutni i umożliwia dodanie ozdabiania przy użyciu znaku +.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Tworzenie projektu zarządzanej struktury rozszerzalności (MEF)

1. Utwórz projekt VSIX języka C#. (W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C# / Extensibility**, a następnie **VSIX Project**.) Nazwij `KeyBindingTest`rozwiązanie .

2. Dodaj szablon elementu ozdoby tekstu edytora do `KeyBindingTest`projektu i nadaj jego nazwę . Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Dodaj następujące odwołania i ustaw **CopyLocal** na: `false`

    Edytor Microsoft.VisualStudio.Editor

    Microsoft.VisualStudio.OLE.Interop

    Microsoft.VisualStudio.Shell.14.0

    Microsoft.VisualStudio.TextManager.Interop

   W pliku klasy KeyBindingTest zmień nazwę klasy na PurpleCornerBox. Użyj żarówki, która pojawi się na lewym marginesie, aby wprowadzić inne odpowiednie zmiany. Wewnątrz konstruktora zmień nazwę warstwy ozdabiania z **KeyBindingTest** na **PurpleCornerBox:**

```csharp
this.layer = view.GetAdornmentLayer("PurpleCornerBox");
```

W pliku klasy KeyBindingTestTextViewCreationListener.cs zmień nazwę AdornmentLayer z **KeyBindingTest** na **PurpleCornerBox**:

```csharp
[Export(typeof(AdornmentLayerDefinition))]
[Name("PurpleCornerBox")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
public AdornmentLayerDefinition editorAdornmentLayer;
```

## <a name="handle-typechar-command"></a>Uchwyt TYPECHAR, polecenie
Przed programem Visual Studio 2017 w wersji 15.6 jedynym sposobem obsługi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> poleceń w rozszerzeniu edytora było zaimplementowanie filtru poleceń opartych. Visual Studio 2017 w wersji 15.6 wprowadzono nowoczesne uproszczone podejście oparte na programach obsługi poleceń edytora. Następne dwie sekcje pokazują, jak obsługiwać polecenia przy użyciu podejścia starszego i nowoczesnego.

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Zdefiniuj filtr poleceń (przed programem Visual Studio 2017 w wersji 15.6)

 Filtr poleceń jest <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>implementacją , który obsługuje polecenie przez wystąpienie ozdabiania.

1. Dodaj plik klasy i `KeyBindingCommandFilter`nadaj jego nazwę .

2. Dodaj następujące za pomocą dyrektyw.

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.OLE.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Text.Editor;

    ```

3. Klasa o nazwie KeyBindingCommandFilter <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>powinna dziedziczyć z .

    ```csharp
    internal class KeyBindingCommandFilter : IOleCommandTarget
    ```

4. Dodaj pola prywatne dla widoku tekstu, następne polecenie w łańcuchu poleceń i flagę reprezentującą, czy filtr polecenia został już dodany.

    ```csharp
    private IWpfTextView m_textView;
    internal IOleCommandTarget m_nextTarget;
    internal bool m_added;
    internal bool m_adorned;
    ```

5. Dodaj konstruktor, który ustawia widok tekstu.

    ```csharp
    public KeyBindingCommandFilter(IWpfTextView textView)
    {
        m_textView = textView;
        m_adorned = false;
    }
    ```

6. Zaimplementuj metodę w `QueryStatus()` następujący sposób.

    ```csharp
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)
    {
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);
    }
    ```

7. Zaimplementuj `Exec()` metodę tak, aby dodawała**+** fioletowe pole do widoku, jeśli wpisany jest znak plus ( ).

    ```csharp
    int IOleCommandTarget.Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)
    {
        if (m_adorned == false)
        {
            char typedChar = char.MinValue;

            if (pguidCmdGroup == VSConstants.VSStd2K && nCmdID == (uint)VSConstants.VSStd2KCmdID.TYPECHAR)
            {
                typedChar = (char)(ushort)Marshal.GetObjectForNativeVariant(pvaIn);
                if (typedChar.Equals('+'))
                {
                    new PurpleCornerBox(m_textView);
                    m_adorned = true;
                }
            }
        }
        return m_nextTarget.Exec(ref pguidCmdGroup, nCmdID, nCmdexecopt, pvaIn, pvaOut);
    }

    ```

## <a name="add-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Dodawanie filtru poleceń (przed programem Visual Studio 2017 w wersji 15.6)
 Dostawca ozdabiania musi dodać filtr poleceń do widoku tekstu. W tym przykładzie dostawca <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> implementuje do nasłuchiwać zdarzeń tworzenia widoku tekstu. Ten dostawca ozdabień eksportuje również warstwę ozdabiania, która definiuje kolejność Z ozdabień.

1. W pliku KeyBindingTestTextViewCreationCreationListener dodaj następujące elementy za pomocą dyrektyw:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.OLE.Interop;
    using Microsoft.VisualStudio.Utilities;
    using Microsoft.VisualStudio.Editor;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.TextManager.Interop;

    ```

2. Aby uzyskać kartę widoku tekstu, <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>należy zaimportować plik .

    ```csharp
    [Import(typeof(IVsEditorAdaptersFactoryService))]
    internal IVsEditorAdaptersFactoryService editorFactory = null;

    ```

3. Zmień <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodę tak, aby `KeyBindingCommandFilter`dodawana jest wartość .

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));
    }
    ```

4. Program `AddCommandFilter` obsługi pobiera kartę widoku tekstu i dodaje filtr poleceń.

    ```csharp
    void AddCommandFilter(IWpfTextView textView, KeyBindingCommandFilter commandFilter)
    {
        if (commandFilter.m_added == false)
        {
            //get the view adapter from the editor factory
            IOleCommandTarget next;
            IVsTextView view = editorFactory.GetViewAdapter(textView);

            int hr = view.AddCommandFilter(commandFilter, out next);

            if (hr == VSConstants.S_OK)
            {
                commandFilter.m_added = true;
                 //you'll need the next target for Exec and QueryStatus
                if (next != null)
                commandFilter.m_nextTarget = next;
            }
        }
    }
    ```

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>Implementowanie programu obsługi poleceń (począwszy od programu Visual Studio 2017 w wersji 15.6)

Najpierw zaktualizuj odwołania nuget projektu, aby odwołać się do najnowszego interfejsu API edytora:

1. Kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Zarządzaj pakietami Nuget**.

2. W **Menedżerze pakietów Nuget**wybierz kartę **Aktualizacje,** zaznacz pole wyboru **Zaznacz wszystkie pakiety,** a następnie wybierz pozycję **Aktualizuj**.

Program obsługi poleceń <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601>jest implementacją , który obsługuje polecenia przez tworzenie wystąpienia ozdabiania.

1. Dodaj plik klasy i `KeyBindingCommandHandler`nadaj jego nazwę .

2. Dodaj następujące za pomocą dyrektyw.

   ```csharp
   using Microsoft.VisualStudio.Commanding;
   using Microsoft.VisualStudio.Text.Editor;
   using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
   using Microsoft.VisualStudio.Utilities;
   using System.ComponentModel.Composition;
   ```

3. Klasa o nazwie KeyBindingCommandHandler `ICommandHandler<TypeCharCommandArgs>`powinna dziedziczyć z , i eksportować go jako: <xref:Microsoft.VisualStudio.Commanding.ICommandHandler>

   ```csharp
   [Export(typeof(ICommandHandler))]
   [ContentType("text")]
   [Name("KeyBindingTest")]
   internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>
   ```

4. Dodaj wyświetlaną nazwę programu obsługi poleceń:

   ```csharp
   public string DisplayName => "KeyBindingTest";
   ```

5. Zaimplementuj metodę w `GetCommandState()` następujący sposób. Ponieważ ten program obsługi poleceń obsługuje polecenie EDYTORA RDZENIA TYPECHAR, może delegować włączenie polecenia do edytora podstawowego.

   ```csharp
   public CommandState GetCommandState(TypeCharCommandArgs args)
   {
       return CommandState.Unspecified;
   }
   ```

6. Zaimplementuj `ExecuteCommand()` metodę tak, aby dodawała**+** fioletowe pole do widoku, jeśli wpisany jest znak plus ( ).

   ```csharp
   public bool ExecuteCommand(TypeCharCommandArgs args, CommandExecutionContext executionContext)
   {
       if (args.TypedChar == '+')
       {
           bool alreadyAdorned = args.TextView.Properties.TryGetProperty(
               "KeyBindingTextAdorned", out bool adorned) && adorned;
           if (!alreadyAdorned)
           {
               new PurpleCornerBox((IWpfTextView)args.TextView);
               args.TextView.Properties.AddProperty("KeyBindingTextAdorned", true);
           }
       }

       return false;
   }
   ```

   7. Skopiuj definicję warstwy ozdabiania z pliku *KeyBindingTestTextViewCreationListener.cs* do *KeyBindingCommandHandler.cs,* a następnie usuń plik *KeyBindingTestTextViewCreationListener.cs:*

   ```csharp
   /// <summary>
   /// Defines the adornment layer for the adornment. This layer is ordered
   /// after the selection layer in the Z-order.
   /// </summary>
   [Export(typeof(AdornmentLayerDefinition))]
   [Name("PurpleCornerBox")]
   [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
   private AdornmentLayerDefinition editorAdornmentLayer;
   ```

## <a name="make-the-adornment-appear-on-every-line"></a>Spraw, aby ozdoba była wyświetlana w każdym wierszu

Oryginalne ozdoby pojawiły się na każdym znaku "a" w pliku tekstowym. Teraz, gdy zmieniliśmy kod, aby dodać ozdoby **+** w odpowiedzi na znak, dodaje ozdoby tylko **+** w wierszu, w którym znak jest wpisywany. Możemy zmienić kod ozdoby tak, aby ozdoba po raz kolejny pojawia się na każdym "a".

W pliku *KeyBindingTest.cs* zmień metodę `CreateVisuals()` na iterację przez wszystkie linie w widoku, aby ozdobić znak "a".

```csharp
private void CreateVisuals(ITextViewLine line)
{
    IWpfTextViewLineCollection textViewLines = this.view.TextViewLines;

    foreach (ITextViewLine textViewLine in textViewLines)
    {
        if (textViewLine.ToString().Contains("a"))
        {
            // Loop through each character, and place a box around any 'a'
            for (int charIndex = textViewLine.Start; charIndex < textViewLine.End; charIndex++)
            {
                if (this.view.TextSnapshot[charIndex] == 'a')
                {
                    SnapshotSpan span = new SnapshotSpan(this.view.TextSnapshot, Span.FromBounds(charIndex, charIndex + 1));
                    Geometry geometry = textViewLines.GetMarkerGeometry(span);
                    if (geometry != null)
                    {
                        var drawing = new GeometryDrawing(this.brush, this.pen, geometry);
                        drawing.Freeze();

                        var drawingImage = new DrawingImage(drawing);
                        drawingImage.Freeze();

                        var image = new Image
                        {
                            Source = drawingImage,
                        };

                        // Align the image with the top of the bounds of the text geometry
                        Canvas.SetLeft(image, geometry.Bounds.Left);
                        Canvas.SetTop(image, geometry.Bounds.Top);

                        this.layer.AddAdornment(AdornmentPositioningBehavior.TextRelative, span, null, image, null);
                    }
                }
            }
        }
    }
}
```

## <a name="build-and-test-the-code"></a>Tworzenie i testowanie kodu

1. Skompiluj rozwiązanie KeyBindingTest i uruchom go w wystąpieniu eksperymentalnym.

2. Tworzenie lub otwieranie pliku tekstowego. Wpisz kilka słów zawierających znak "a", **+** a następnie wpisz w dowolnym miejscu w widoku tekstu.

     Fioletowy kwadrat powinien pojawić się na każdym znaku "a" w pliku.
