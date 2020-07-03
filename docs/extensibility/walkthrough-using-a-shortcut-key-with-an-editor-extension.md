---
title: 'Przewodnik: używanie klawisza skrótu z rozszerzeniem edytora | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 094cb590d5b2a3bf062916985bfc61b1cf76d365
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904404"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>Przewodnik: używanie klawisza skrótu z rozszerzeniem edytora
Możesz odpowiedzieć na skróty klawiaturowe w rozszerzeniu edytora. W poniższym przewodniku przedstawiono sposób dodawania zakończenia wyświetlania widoku do widoku tekstu przy użyciu klawisza skrótu. Ten przewodnik jest oparty na szablonie edytora autodefiniowania okienka ekranu, który umożliwia dodanie definiowania układu przy użyciu znaku +.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dołączana jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Tworzenie projektu Managed Extensibility Framework (MEF)

1. Utwórz projekt VSIX języka C#. (W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C#/rozszerzalność**, a następnie **Projekt VSIX**). Nadaj nazwę rozwiązanie `KeyBindingTest` .

2. Dodaj szablon elementu zakończenia tekstu edytora do projektu i nadaj mu nazwę `KeyBindingTest` . Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Dodaj następujące odwołania i ustaw **CopyLocal** na `false` :

    Microsoft. VisualStudio. Editor

    Microsoft. VisualStudio. OLE. Interop

    Microsoft. VisualStudio. Shell. 14.0

    Microsoft. VisualStudio. TextManager. Interop

   W pliku klasy KeyBindingTest Zmień nazwę klasy na PurpleCornerBox. Użyj żarówki, która pojawia się na lewym marginesie, aby wprowadzić inne odpowiednie zmiany. Wewnątrz konstruktora Zmień nazwę warstwy zakończenia z **KeyBindingTest** na **PurpleCornerBox**:

```csharp
this.layer = view.GetAdornmentLayer("PurpleCornerBox");
```

W pliku klasy KeyBindingTestTextViewCreationListener.cs Zmień nazwę AdornmentLayer z **KeyBindingTest** na **PurpleCornerBox**:

```csharp
[Export(typeof(AdornmentLayerDefinition))]
[Name("PurpleCornerBox")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
public AdornmentLayerDefinition editorAdornmentLayer;
```

## <a name="handle-typechar-command"></a>Obsługa polecenia TYPECHAR
Przed zainstalowaniem programu Visual Studio 2017 w wersji 15,6 jedynym sposobem obsługi poleceń w rozszerzeniu edytora była implementacja <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> filtru poleceń opartych na protokole. W programie Visual Studio 2017 w wersji 15,6 wprowadzono nowoczesne uproszczone podejście na podstawie programów obsługi poleceń edytora. W następnych dwóch sekcjach pokazano, jak obsłużyć polecenie przy użyciu metody starszej i nowoczesnej.

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Zdefiniuj filtr poleceń (wcześniejszy niż program Visual Studio 2017 w wersji 15,6)

 Filtr polecenia jest implementacją <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , która obsługuje polecenie przez utworzenie wystąpienia.

1. Dodaj plik klasy i nadaj mu nazwę `KeyBindingCommandFilter` .

2. Dodaj następujące dyrektywy using.

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.OLE.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Text.Editor;

    ```

3. Klasa o nazwie KeyBindingCommandFilter powinna dziedziczyć po elemencie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

    ```csharp
    internal class KeyBindingCommandFilter : IOleCommandTarget
    ```

4. Dodaj pola prywatne dla widoku tekstu, następne polecenie w łańcuchu poleceń i flagę, aby wskazać, czy filtr poleceń został już dodany.

    ```csharp
    private IWpfTextView m_textView;
    internal IOleCommandTarget m_nextTarget;
    internal bool m_added;
    internal bool m_adorned;
    ```

5. Dodaj konstruktora, który ustawia widok tekstu.

    ```csharp
    public KeyBindingCommandFilter(IWpfTextView textView)
    {
        m_textView = textView;
        m_adorned = false;
    }
    ```

6. Zaimplementuj `QueryStatus()` metodę w następujący sposób.

    ```csharp
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)
    {
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);
    }
    ```

7. Zaimplementuj `Exec()` metodę, aby dodać purpurowe pole do widoku, jeśli **+** wpisano znak plus ().

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

## <a name="add-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Dodaj filtr polecenia (wcześniejszy niż program Visual Studio 2017 w wersji 15,6)
 Dostawca modułu definiowania układu musi dodać filtr polecenia do widoku tekstu. W tym przykładzie dostawca implementuje, <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> aby nasłuchiwać zdarzeń tworzenia widoku tekstu. Ten dostawca zawiera również eksport warstwy zakończenia, która definiuje porządek osi Z.

1. W pliku KeyBindingTestTextViewCreationListener Dodaj następujące dyrektywy using:

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

2. Aby uzyskać kartę widoku tekstu, należy zaimportować <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> .

    ```csharp
    [Import(typeof(IVsEditorAdaptersFactoryService))]
    internal IVsEditorAdaptersFactoryService editorFactory = null;

    ```

3. Zmień <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodę tak, aby dodała `KeyBindingCommandFilter` .

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));
    }
    ```

4. `AddCommandFilter`Program obsługi pobiera adapter widoku tekstu i dodaje filtr poleceń.

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

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>Zaimplementuj procedurę obsługi poleceń (począwszy od programu Visual Studio 2017 w wersji 15,6)

Najpierw zaktualizuj odwołania NuGet projektu, aby odwołać się do najnowszego interfejsu API edytora:

1. Kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.

2. W **Menedżerze pakietów NuGet**wybierz kartę **aktualizacje** , zaznacz pole wyboru **zaznacz wszystkie pakiety** , a następnie wybierz pozycję **Aktualizuj**.

Program obsługi poleceń jest implementacją <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601> , która obsługuje polecenie, tworząc Tworzenie modułu definiowania układu.

1. Dodaj plik klasy i nadaj mu nazwę `KeyBindingCommandHandler` .

2. Dodaj następujące dyrektywy using.

   ```csharp
   using Microsoft.VisualStudio.Commanding;
   using Microsoft.VisualStudio.Text.Editor;
   using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
   using Microsoft.VisualStudio.Utilities;
   using System.ComponentModel.Composition;
   ```

3. Klasa o nazwie KeyBindingCommandHandler powinna dziedziczyć z `ICommandHandler<TypeCharCommandArgs>` i wyeksportować ją jako <xref:Microsoft.VisualStudio.Commanding.ICommandHandler> :

   ```csharp
   [Export(typeof(ICommandHandler))]
   [ContentType("text")]
   [Name("KeyBindingTest")]
   internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>
   ```

4. Dodaj nazwę wyświetlaną programu obsługi poleceń:

   ```csharp
   public string DisplayName => "KeyBindingTest";
   ```

5. Zaimplementuj `GetCommandState()` metodę w następujący sposób. Ponieważ ten program obsługi poleceń obsługuje podstawowe polecenie edytora TYPECHAR, może delegować włączenie polecenia do podstawowego edytora.

   ```csharp
   public CommandState GetCommandState(TypeCharCommandArgs args)
   {
       return CommandState.Unspecified;
   }
   ```

6. Zaimplementuj `ExecuteCommand()` metodę, aby dodać purpurowe pole do widoku, jeśli **+** wpisano znak plus ().

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

   7. Skopiuj definicję warstwy zakończenia z pliku *KeyBindingTestTextViewCreationListener.cs* do *KeyBindingCommandHandler.cs* , a następnie usuń plik *KeyBindingTestTextViewCreationListener.cs* :

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

## <a name="make-the-adornment-appear-on-every-line"></a>Utwórz umieszczanie w każdym wierszu

Oryginalny moduł definiowania układu pojawił się w każdym znaku "a" w pliku tekstowym. Teraz, gdy kod został zmieniony w celu dodania zakończenia w odpowiedzi na **+** znak, dodaje znakowanie tylko w wierszu, w którym **+** jest wpisana wartość. Możemy zmienić kod zakończenia tak, aby po każdym z nich pojawił się moduł definiowania układu.

W pliku *KeyBindingTest.cs* Zmień `CreateVisuals()` metodę, aby wykonać iterację we wszystkich wierszach widoku, aby dekorować znak "a".

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

## <a name="build-and-test-the-code"></a>Kompiluj i Testuj kod

1. Skompiluj rozwiązanie KeyBindingTest i uruchom je w eksperymentalnym wystąpieniu.

2. Utwórz lub Otwórz plik tekstowy. Wpisz kilka wyrazów zawierających znak "a", a następnie wpisz **+** dowolne miejsce w widoku tekstu.

     Purpurowy kwadrat powinien pojawić się w każdym znaku "a" w pliku.
