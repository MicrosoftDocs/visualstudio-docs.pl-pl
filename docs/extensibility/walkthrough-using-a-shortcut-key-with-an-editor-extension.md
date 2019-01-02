---
title: 'Przewodnik: Używanie klawisza skrótu z rozszerzeniem edytora | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e669b86a84f21dd6187558fc0a853c875d5d2e71
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53953014"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>Przewodnik: Użyj klawisza skrótu z rozszerzeniem edytora
Klawisze skrótów można odpowiedzieć w rozszerzeniu edytora. Następujące Instruktaż pokazuje, jak dodać zakończeń widok na widok tekstu przy użyciu klawisza skrótu. Ten przewodnik jest oparty na szablonie edytora zakończeń okienka ekranu, i umożliwia dodawanie zakończeń przy użyciu + znak.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, nie instaluj programu Visual Studio SDK z Centrum pobierania. Został on uwzględniony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-managed-extensibility-framework-mef-project"></a>Utwórz projekt Framework (MEF) zarządzanych rozszerzeń  
  
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

W pliku klasy KeyBindingTestTextViewCreationListener.cs, Zmień nazwę AdornmentLayer z **KeyBindingTest** do **PurpleCornerBox**:
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  

## <a name="handle-typechar-command"></a>Polecenie TYPECHAR uchwytu
Przed Visual Studio 2017 w wersji 15.6, jedynym sposobem obsługi poleceń w rozszerzenia edytora została Implementowanie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> na podstawie filtru polecenia. Visual Studio 2017 w wersji 15.6 wprowadzono nowoczesnej uproszczone podejście oparte na programy obsługi poleceń edytora. W dwóch następnych sekcjach pokazują sposób obsługi polecenia przy użyciu zarówno starsze i nowoczesne podejście.

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Zdefiniuj filtr polecenia (przed Visual Studio 2017 w wersji 15.6)

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
  
    ```csharp  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7.  Implementowanie `Exec()` metodę, tak że dodaje purpurowy pola do widoku, jeśli znak plus (**+**) wpisany znak.  
  
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
  
## <a name="add-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Dodaj filtr polecenia (przed Visual Studio 2017 w wersji 15.6)
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
  
2.  Aby uzyskać karty widoku tekstu, należy zaimportować <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>.  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
3.  Zmiana <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodę, tak że dodaje `KeyBindingCommandFilter`.  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
4.  `AddCommandFilter` Obsługi pobiera karty widoku tekstu i dodaje filtr polecenia.  
  
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

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>Implementowanie program obsługi poleceń (począwszy od programu Visual Studio 2017 w wersji 15.6)

Najpierw zaktualizuj odwołań Nuget projektu do odwołania najnowsze Edytor interfejsu API:

1. Kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Zarządzaj pakietami Nuget**.

2. W **Menedżera pakietów Nuget**, wybierz opcję **aktualizacje** wybierz kartę **wybrać wszystkie pakiety** pole wyboru, a następnie wybierz pozycję **aktualizacji**.

Program obsługi poleceń jest implementacją <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601>, która obsługuje polecenie przez utworzenie wystąpienia zakończeń.  
  
1. Dodaj plik klasy i nadaj mu nazwę `KeyBindingCommandHandler`.  
  
2. Dodaj następujące instrukcje using.  
  
   ```csharp  
   using Microsoft.VisualStudio.Commanding;
   using Microsoft.VisualStudio.Text.Editor;
   using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
   using Microsoft.VisualStudio.Utilities;
   using System.ComponentModel.Composition;   
   ```  
  
3. Klasa o nazwie KeyBindingCommandHandler powinien dziedziczyć `ICommandHandler<TypeCharCommandArgs>`i wyeksportuj go jako <xref:Microsoft.VisualStudio.Commanding.ICommandHandler>:
  
   ```csharp  
   [Export(typeof(ICommandHandler))]
   [ContentType("text")]
   [Name("KeyBindingTest")]
   internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>  
   ```  
  
4. Dodaj nazwę wyświetlaną program obsługi poleceń:  
  
   ```csharp  
   public string DisplayName => "KeyBindingTest";
   ```  
    
5. Implementowanie `GetCommandState()` metody w następujący sposób. Ponieważ ten program obsługi poleceń obsługuje polecenie TYPECHAR Edytor rdzeni, można delegować, umożliwiając polecenie, aby podstawowy edytor.
  
   ```csharp  
   public CommandState GetCommandState(TypeCharCommandArgs args)
   {
       return CommandState.Unspecified;
   } 
   ```  
  
6. Implementowanie `ExecuteCommand()` metodę, tak że dodaje purpurowy pola do widoku, jeśli znak plus (**+**) wpisany znak. 
  
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
   7. Skopiuj definicję warstwy zakończeń z *KeyBindingTestTextViewCreationListener.cs* plik *KeyBindingCommandHandler.cs* , a następnie usuń  *KeyBindingTestTextViewCreationListener.cs* pliku:
 
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

## <a name="make-the-adornment-appear-on-every-line"></a>Wprowadź zakończeń są wyświetlane w każdym wierszu  

Oryginalny zakończeń pojawiły się na każdy znak "" w pliku tekstowym. Teraz, że dokonaliśmy zmiany kodu w celu dodania zakończeń w odpowiedzi na **+** znak dodaje zakończeń tylko w wierszu gdzie **+** wpisany znak. Możemy zmienić kod zakończeń, czemu zakończeń, jeszcze raz pojawia się w każdym "".  
  
W *KeyBindingTest.cs* pliku, zmień `CreateVisuals()` metody iteracyjne przeglądanie wszystkich wierszy w widoku do dekorowania znak "".  
  
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
  
1.  Skompiluj rozwiązanie KeyBindingTest i uruchom go w doświadczalnym wystąpieniu.  
  
2.  Utwórz lub Otwórz plik tekstowy. Wpisz wyrazy, niektóre zawierającą znak "", a następnie wpisz **+** w widoku tekstu w dowolnym miejscu.  
  
     Purpurowa kwadrat powinny pojawić się na każdym "" znak w pliku.
