---
title: 'Przewodnik: używanie klawisza skrótu z rozszerzeniem edytora | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5c9cb20bafa552c47a2f599d12e6b66fdb2bde59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201949"
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>Przewodnik: używanie klawisza skrótu z rozszerzeniem edytora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz odpowiedzieć na skróty klawiaturowe w rozszerzeniu edytora. W poniższym przewodniku przedstawiono sposób dodawania zakończenia wyświetlania widoku do widoku tekstu przy użyciu klawisza skrótu. Ten przewodnik jest oparty na szablonie edytora autodefiniowania okienka ekranu, który umożliwia dodanie definiowania układu przy użyciu znaku +.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Tworzenie projektu Managed Extensibility Framework (MEF)  
  
1. Utwórz projekt VSIX języka C#. (W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C#/rozszerzalność**, a następnie **Projekt VSIX**). Nadaj nazwę rozwiązanie `KeyBindingTest` .  
  
2. Dodaj szablon elementu zakończenia tekstu edytora do projektu i nadaj mu nazwę `KeyBindingTest` . Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Dodaj następujące odwołania i ustaw **CopyLocal** na `false` :  
  
    Microsoft. VisualStudio. Editor  
  
    Microsoft. VisualStudio. OLE. Interop  
  
    Microsoft. VisualStudio. Shell. 14.0  
  
    Microsoft. VisualStudio. TextManager. Interop  
  
   W pliku klasy KeyBindingTest Zmień nazwę klasy na PurpleCornerBox. Użyj żarówki, która pojawia się na lewym marginesie, aby wprowadzić inne odpowiednie zmiany. Wewnątrz konstruktora Zmień nazwę warstwy zakończenia z **KeyBindingTest** na **PurpleCornerBox**:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  
  
## <a name="defining-the-command-filter"></a>Definiowanie filtru poleceń  
 Filtr polecenia jest implementacją <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , która obsługuje polecenie przez utworzenie wystąpienia.  
  
1. Dodaj plik klasy i nadaj mu nazwę `KeyBindingCommandFilter` .  
  
2. Dodaj następujące instrukcje using.  
  
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
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7. Zaimplementuj `Exec()` metodę, tak aby po wpisaniu znaku + został dodany purpurowy prostokąt do widoku.  
  
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
  
## <a name="adding-the-command-filter"></a>Dodawanie filtru poleceń  
 Dostawca modułu definiowania układu musi dodać filtr polecenia do widoku tekstu. W tym przykładzie dostawca implementuje, <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> aby nasłuchiwać zdarzeń tworzenia widoku tekstu. Ten dostawca zawiera również eksport warstwy zakończenia, która definiuje porządek osi Z.  
  
1. W pliku KeyBindingTestTextViewCreationListener Dodaj następujące instrukcje using:  
  
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
  
2. W definicji warstwy definiowania układu Zmień nazwę AdornmentLayer z **KeyBindingTest** na **PurpleCornerBox**.  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3. Aby uzyskać kartę widoku tekstu, należy zaimportować <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> .  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4. Zmień <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodę tak, aby dodała `KeyBindingCommandFilter` .  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5. `AddCommandFilter`Program obsługi pobiera adapter widoku tekstu i dodaje filtr poleceń.  
  
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
  
## <a name="making-the-adornment-appear-on-every-line"></a>W każdym wierszu pojawia się okno definiowania układu  
 Oryginalny moduł definiowania układu pojawił się w każdym znaku "a" w pliku tekstowym. Po zmianie kodu w celu dodania modułu definiowania układu w odpowiedzi na znak "+", zostanie dodany moduł definiowania układu tylko w wierszu, w którym jest wpisana wartość "+". Możemy zmienić kod zakończenia tak, aby po każdym z nich pojawił się moduł definiowania układu.  
  
 W pliku KeyBindingTest.cs Zmień metodę moje wizualizacje (), aby wykonać iterację we wszystkich wierszach widoku, aby dekorować znak "a".  
  
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
  
## <a name="building-and-testing-the-code"></a>Kompilowanie i testowanie kodu  
  
1. Skompiluj rozwiązanie KeyBindingTest i uruchom je w eksperymentalnym wystąpieniu.  
  
2. Utwórz lub Otwórz plik tekstowy. Wpisz słowa zawierające znak "a", a następnie wpisz + wszędzie w widoku tekstu.  
  
     Purpurowy kwadrat powinien pojawić się w każdym znaku "a" w pliku.
