---
title: 'Przewodnik: Używanie klawisza skrótu z rozszerzeniem edytora | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: b40c0590b19b555f757af1e0a38481b0b245c07d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54763020"
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>Przewodnik: Używanie klawisza skrótu z rozszerzeniem edytora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Klawisze skrótów można odpowiedzieć w rozszerzeniu edytora. Następujące Instruktaż pokazuje, jak dodać zakończeń widok na widok tekstu przy użyciu klawisza skrótu. Ten przewodnik jest oparty na szablonie edytora zakończeń okienka ekranu, i umożliwia dodawanie zakończeń przy użyciu + znak.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Tworzenie projektu Framework (MEF) zarządzanych rozszerzeń  
  
1. Utwórz projekt VSIX języka C#. (W **nowy projekt** okno dialogowe, wybierz opcję **Visual C# / rozszerzalności**, następnie **projekt VSIX**.) Nazwij rozwiązanie `KeyBindingTest`.  
  
2. Szablon elementu zakończeń tekstu Edytor umożliwia dodanie do projektu i nadaj mu nazwę `KeyBindingTest`. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Dodaj następujące odwołania i ustaw **CopyLocal** do `false`:  
  
    Microsoft.VisualStudio.Editor  
  
    Microsoft.VisualStudio.OLE.Interop  
  
    Microsoft.VisualStudio.Shell.14.0  
  
    Microsoft.VisualStudio.TextManager.Interop  
  
   W pliku klasy KeyBindingTest należy zmienić nazwę klasy do PurpleCornerBox. Umożliwia żarówki, która pojawia się na lewym marginesie wprowadzić odpowiednie zmiany. W konstruktorze, Zmień nazwę warstwy zakończeń z **KeyBindingTest** do **PurpleCornerBox**:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  
  
## <a name="defining-the-command-filter"></a>Definiowanie filtrów polecenia  
 Filtr polecenia jest implementacją <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, która obsługuje polecenie przez utworzenie wystąpienia zakończeń.  
  
1.  Dodaj plik klasy i nadaj mu nazwę `KeyBindingCommandFilter`.  
  
2.  Dodaj następujące instrukcje using.  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3.  Klasa o nazwie KeyBindingCommandFilter powinien dziedziczyć <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
    ```csharp  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4.  Dodaj pola prywatne dla widoku tekstu, następnego polecenia w łańcuchu polecenia i flagi do reprezentowania, czy filtr polecenia został już dodany.  
  
    ```csharp  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5.  Dodaj Konstruktor, który ustawia widok tekstu.  
  
    ```csharp  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6.  Implementowanie `QueryStatus()` metody w następujący sposób.  
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7.  Implementowanie `Exec()` metodę, tak że pole jest dodawane do purpurowy do widoku Jeśli + wpisany znak.  
  
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
  
## <a name="adding-the-command-filter"></a>Dodawanie filtru polecenia  
 Dostawca zakończeń należy dodać polecenie Filtr do widoku tekstu. W tym przykładzie implementuje dostawcę <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> do nasłuchiwania zdarzeń tworzenia widoku tekstu. Ten dostawca zakończeń Eksportuje również warstwy zakończeń, definiujący porządek zakończeń.  
  
1.  W pliku KeyBindingTestTextViewCreationListener, Dodaj następujące instrukcje using:  
  
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
  
2.  W definicji warstwy zakończeń, Zmień nazwę AdornmentLayer z **KeyBindingTest** do **PurpleCornerBox**.  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3.  Aby uzyskać karty widoku tekstu, należy zaimportować <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>.  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4.  Zmiana <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodę, tak że dodaje `KeyBindingCommandFilter`.  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5.  `AddCommandFilter` Obsługi pobiera karty widoku tekstu i dodaje filtr polecenia.  
  
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
  
## <a name="making-the-adornment-appear-on-every-line"></a>Tworzenie zakończeń są wyświetlane w każdym wierszu  
 Oryginalny zakończeń pojawiły się na każdy znak "" w pliku tekstowym. Teraz, że dokonaliśmy zmiany kodu w celu dodania zakończeń w odpowiedzi na znak "+", dodaje zakończeń tylko w wierszu gdzie '+' został wpisany. Możemy zmienić kod zakończeń, czemu zakończeń, jeszcze raz pojawia się w każdym "".  
  
 W pliku KeyBindingTest.cs zmienić metodę CreateVisuals() do iterowania po wszystkich wierszy w widoku do dekorowania znak "".  
  
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
  
## <a name="building-and-testing-the-code"></a>Tworzenie i testowanie kodu  
  
1.  Skompiluj rozwiązanie KeyBindingTest i uruchom go w doświadczalnym wystąpieniu.  
  
2.  Utwórz lub Otwórz plik tekstowy. Wpisz wyrazy, niektóre zawierającą znak "", a następnie wpisz i w dowolnym miejscu w widoku tekstu.  
  
     Purpurowa kwadrat powinny pojawić się na każdym "" znak w pliku.
