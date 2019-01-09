---
title: 'Przewodnik: Używanie polecenia programu PowerShell z rozszerzeniem edytora | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b62ffce08ecf5b6397bdda0b1f9fb6c1b83d7b63
ms.sourcegitcommit: 73861cd0ea92e50a3be1ad2a0ff0a7b07b057a1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54154340"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>Przewodnik: Użyj polecenia powłoki z rozszerzeniem edytora
Z pakietu VSPackage możesz dodać funkcje, takie jak polecenia menu do edytora. W tym instruktażu przedstawiono sposób dodawania zakończeń widoku tekstu w edytorze za pomocą wywołania polecenia menu.  
  
 W tym przewodniku zademonstrowano użycie pakietu VSPackage wraz z część Managed Extensibility Framework (MEF). Aby zarejestrować polecenia menu z powłoki programu Visual Studio, należy użyć pakietu VSPackage. Ponadto możesz użyć polecenia uzyskać dostęp do części składnik MEF.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, nie instaluj programu Visual Studio SDK z Centrum pobierania. Został on uwzględniony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-an-extension-with-a-menu-command"></a>Tworzenie rozszerzenia za pomocą polecenia menu  
 Tworzenie pakietu VSPackage, który umieszcza polecenie menu o nazwie **Dodaj zakończeń** na **narzędzia** menu.  
  
1.  Utwórz projekt VSIX języka C# o nazwie `MenuCommandTest`i Dodaj nazwę polecenia niestandardowego szablonu elementu **AddAdornment**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Zostanie otwarte rozwiązanie o nazwie MenuCommandTest. Plik MenuCommandTestPackage zawiera kod, który tworzy polecenie menu i umieszcza go w **narzędzia** menu. W tym momencie polecenia powoduje po prostu się pojawić okno komunikatu. Dalszych krokach pokazują, jak można zmienić, aby wyświetlić zakończeń komentarz.  
  
3.  Otwórz *source.extension.vsixmanifest* plik w edytorze manifestu VSIX. `Assets` Karty powinny mieć wiersz dla Microsoft.VisualStudio.VsPackage o nazwie MenuCommandTest.  
  
4.  Zapisz i Zamknij *source.extension.vsixmanifest* pliku.  
  
## <a name="add-a-mef-extension-to-the-command-extension"></a>Dodaj rozszerzenie MEF do rozszerzenia polecenia  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł rozwiązania, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **nowy projekt**. W **Dodaj nowy projekt** okno dialogowe, kliknij przycisk **rozszerzalności** w obszarze **Visual C#**, następnie **projekt VSIX**. Nadaj projektowi nazwę `CommentAdornmentTest`.  
  
2.  Ponieważ ten projekt będzie współpracować z zestawu o silnej nazwie pakietu VSPackage, musi podpisać zestaw. Można użyć ponownie już utworzony dla zestawu pakietu VSPackage plik klucza.  
  
    1.  Otwórz właściwości projektu i wybierz **podpisywanie** kartę.  
  
    2.  Wybierz **Podpisz zestaw**.  
  
    3.  W obszarze **wybierz plik klucza o silnej nazwie**, wybierz opcję *Key.snk* pliku, który został wygenerowany dla zestawu MenuCommandTest.  
  
## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>Zapoznaj się z rozszerzeniem MEF projektu pakietu VSPackage  
 Ponieważ dodajesz składnik MEF do pakietu VSPackage, należy określić obu rodzajów zasobów w manifeście.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat MEF, zobacz [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).  
  
### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>Aby odwołać się do składnik listy MEF projektu pakietu VSPackage  
  
1.  W projekcie MenuCommandTest Otwórz *source.extension.vsixmanifest* plik w edytorze manifestu VSIX.  
  
2.  Na **zasoby** kliknij pozycję **New**.  
  
3.  W **typu** wybierz **Microsoft.VisualStudio.MefComponent**.  
  
4.  W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.  
  
5.  W **projektu** wybierz **CommentAdornmentTest**.  
  
6.  Zapisz i Zamknij *source.extension.vsixmanifest* pliku.  
  
7.  Upewnij się, że projekt MenuCommandTest ma odwołanie do projektu CommentAdornmentTest.  
  
8.  W projekcie CommentAdornmentTest Ustaw projekt do utworzenia zestawu. W **Eksploratora rozwiązań**, wybierz projekt i poszukaj w **właściwości** okno **danych wyjściowych kompilacji kopiowania do OutputDirectory** właściwości i ustaw ją na **true**.  
  
## <a name="define-a-comment-adornment"></a>Zdefiniuj zakończeń komentarz  
 Zakończeń komentarza, sama składa się z <xref:Microsoft.VisualStudio.Text.ITrackingSpan> który śledzi zaznaczonego tekstu, a niektóre ciągi, które reprezentują autor i opis tekstu.  
  
#### <a name="to-define-a-comment-adornment"></a>Aby zdefiniować zakończeń komentarz  
  
1.  W projekcie CommentAdornmentTest, Dodaj nowy plik klasy, a następnie nadaj mu nazwę `CommentAdornment`.  
  
2.  Dodaj następujące odwołania:  
  
    1.  Microsoft.VisualStudio.CoreUtility  
  
    2.  Microsoft.VisualStudio.Text.Data  
  
    3.  Microsoft.VisualStudio.Text.Logic  
  
    4.  Microsoft.VisualStudio.Text.UI  
  
    5.  Microsoft.VisualStudio.Text.UI.Wpf  
  
    6.  System.ComponentModel.Composition  
  
    7.  PresentationCore  
  
    8.  PresentationFramework  
  
    9. WindowsBase  
  
3.  Dodaj następujący kod `using` instrukcji.  
  
    ```csharp
    using Microsoft.VisualStudio.Text;  
    ```  
  
4.  Ten plik powinien zawierać klasę o nazwie `CommentAdornment`.  
  
    ```csharp  
    internal class CommentAdornment  
    ```  
  
5.  Dodaj trzy pola `CommentAdornment` klasy dla <xref:Microsoft.VisualStudio.Text.ITrackingSpan>, autor i opis.  
  
    ```csharp  
    public readonly ITrackingSpan Span;  
    public readonly string Author;  
    public readonly string Text;  
    ```  
  
6.  Dodaj Konstruktor, który inicjuje pola.  
  
    ```csharp  
    public CommentAdornment(SnapshotSpan span, string author, string text)  
    {  
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);  
        this.Author = author;  
        this.Text = text;  
    }  
    ```  
  
## <a name="create-a-visual-element-for-the-adornment"></a>Tworzenie elementu wizualnego do zakończeń  
 Zdefiniuj element wizualny dla Twojego zakończeń. W ramach tego przewodnika należy zdefiniować formant, który dziedziczy z klasy Windows Presentation Foundation (WPF) <xref:System.Windows.Controls.Canvas>.  
  
1.  Utwórz klasę w projekcie CommentAdornmentTest i nadaj mu nazwę `CommentBlock`.  
  
2.  Dodaj następujący kod `using` instrukcji.  
  
    ```csharp  
    using Microsoft.VisualStudio.Text;  
    using System;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Media;  
    using System.Windows.Shapes;  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Utilities;  
    ```  
  
3.  Wprowadź `CommentBlock` klasa dziedziczy <xref:System.Windows.Controls.Canvas>.  
  
    ```csharp  
    internal class CommentBlock : Canvas  
    { }  
    ```  
  
4.  Dodaj niektóre pola prywatne, aby zdefiniować visual aspektów zakończeń.  
  
    ```csharp  
    private Geometry textGeometry;  
    private Grid commentGrid;  
    private static Brush brush;  
    private static Pen solidPen;  
    private static Pen dashPen;  
    ```  
  
5.  Dodaj Konstruktor, który definiuje zakończeń komentarz, a następnie dodaje odpowiedni tekst.  
  
    ```csharp  
    public CommentBlock(double textRightEdge, double viewRightEdge,   
            Geometry newTextGeometry, string author, string body)  
    {  
        if (brush == null)  
        {  
            brush = new SolidColorBrush(Color.FromArgb(0x20, 0x00, 0xff, 0x00));  
            brush.Freeze();  
            Brush penBrush = new SolidColorBrush(Colors.Green);  
            penBrush.Freeze();  
            solidPen = new Pen(penBrush, 0.5);  
            solidPen.Freeze();  
            dashPen = new Pen(penBrush, 0.5);  
            dashPen.DashStyle = DashStyles.Dash;  
            dashPen.Freeze();  
        }  
  
        this.textGeometry = newTextGeometry;  
  
        TextBlock tb1 = new TextBlock();  
        tb1.Text = author;  
        TextBlock tb2 = new TextBlock();  
        tb2.Text = body;  
  
        const int MarginWidth = 8;  
        this.commentGrid = new Grid();  
        this.commentGrid.RowDefinitions.Add(new RowDefinition());  
        this.commentGrid.RowDefinitions.Add(new RowDefinition());  
        ColumnDefinition cEdge = new ColumnDefinition();  
        cEdge.Width = new GridLength(MarginWidth);  
        ColumnDefinition cEdge2 = new ColumnDefinition();  
        cEdge2.Width = new GridLength(MarginWidth);  
        this.commentGrid.ColumnDefinitions.Add(cEdge);  
        this.commentGrid.ColumnDefinitions.Add(new ColumnDefinition());  
        this.commentGrid.ColumnDefinitions.Add(cEdge2);  
  
        System.Windows.Shapes.Rectangle rect = new System.Windows.Shapes.Rectangle();  
        rect.RadiusX = 6;  
        rect.RadiusY = 3;  
        rect.Fill = brush;  
        rect.Stroke = Brushes.Green;  
  
            Size inf = new Size(double.PositiveInfinity, double.PositiveInfinity);  
            tb1.Measure(inf);  
            tb2.Measure(inf);  
            double middleWidth = Math.Max(tb1.DesiredSize.Width, tb2.DesiredSize.Width);  
            this.commentGrid.Width = middleWidth + 2 * MarginWidth;  
  
        Grid.SetColumn(rect, 0);  
        Grid.SetRow(rect, 0);  
        Grid.SetRowSpan(rect, 2);  
        Grid.SetColumnSpan(rect, 3);  
        Grid.SetRow(tb1, 0);  
        Grid.SetColumn(tb1, 1);  
        Grid.SetRow(tb2, 1);  
        Grid.SetColumn(tb2, 1);  
        this.commentGrid.Children.Add(rect);  
        this.commentGrid.Children.Add(tb1);  
        this.commentGrid.Children.Add(tb2);  
  
        Canvas.SetLeft(this.commentGrid, Math.Max(viewRightEdge - this.commentGrid.Width - 20.0, textRightEdge + 20.0));  
        Canvas.SetTop(this.commentGrid, textGeometry.GetRenderBounds(solidPen).Top);  
  
        this.Children.Add(this.commentGrid);  
    }  
    ```  
  
6.  Także implementować <xref:System.Windows.Controls.Panel.OnRender%2A> program obsługi zdarzeń, który rysuje zakończeń.  
  
    ```csharp  
    protected override void OnRender(DrawingContext dc)  
    {  
        base.OnRender(dc);  
        if (this.textGeometry != null)  
        {  
            dc.DrawGeometry(brush, solidPen, this.textGeometry);  
            Rect textBounds = this.textGeometry.GetRenderBounds(solidPen);  
            Point p1 = new Point(textBounds.Right, textBounds.Bottom);  
            Point p2 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid) - 20.0, p1.X), p1.Y);  
            Point p3 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid), p1.X), (Canvas.GetTop(this.commentGrid) + p1.Y) * 0.5);  
            dc.DrawLine(dashPen, p1, p2);  
            dc.DrawLine(dashPen, p2, p3);  
        }  
    }  
    ```  
  
## <a name="add-an-iwpftextviewcreationlistener"></a>Dodaj IWpfTextViewCreationListener  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> Jest używanego do nasłuchiwania, aby wyświetlić zdarzenia tworzenia część MEF.  
  
1.  Dodaj plik klasy do projektu CommentAdornmentTest i nadaj mu nazwę `Connector`.  
  
2.  Dodaj następujący kod `using` instrukcji.  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Utilities;  
    ```  
  
3.  Deklarowanie klasy, która implementuje <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>i wyeksportuj go z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> z "text" i <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> z <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>. Atrybut typu zawartości określa typ zawartości, do której stosują się składnika. Typ tekstu jest typem podstawowym dla wszystkich typów plików innego niż binarny. W związku z tym prawie każdy widok tekstu, który jest tworzony będzie tego typu. Atrybut roli w widoku tekstu określa rodzaj widoku tekstu, którego dotyczy ten składnik. Role widoku tekstu dokumentu zwykle Pokaż tekst, który składa się z wierszy i jest przechowywany w pliku.  
  
     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]  
  
4.  Implementowanie <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodę, tak że wywołuje statyczną `Create()` zdarzenia `CommentAdornmentManager`.  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        CommentAdornmentManager.Create(textView);  
    }  
    ```  
  
5.  Dodaj metodę, którego można użyć w celu wykonania tego polecenia.  
  
    ```csharp  
    static public void Execute(IWpfTextViewHost host)  
    {  
        IWpfTextView view = host.TextView;  
        //Add a comment on the selected text.   
        if (!view.Selection.IsEmpty)  
        {  
            //Get the provider for the comment adornments in the property bag of the view.  
            CommentAdornmentProvider provider = view.Properties.GetProperty<CommentAdornmentProvider>(typeof(CommentAdornmentProvider));  
  
            //Add some arbitrary author and comment text.   
            string author = System.Security.Principal.WindowsIdentity.GetCurrent().Name;  
            string comment = "Four score....";  
  
            //Add the comment adornment using the provider.  
            provider.Add(view.Selection.SelectedSpans[0], author, comment);  
        }  
    }  
    ```  
  
## <a name="define-an-adornment-layer"></a>Zdefiniuj zakończeń warstwy  
 Aby dodać nowe zakończeń, należy zdefiniować warstwy zakończeń.  
  
### <a name="to-define-an-adornment-layer"></a>Aby zdefiniować warstwy zakończeń  
  
1.  W `Connector` klasy, Zadeklaruj publiczne pole o typie <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>i wyeksportuj go z <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , który określa unikatową nazwę warstwy zakończeń i <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> definiuje relację porządku osi Z tą warstwą zakończeń w innym tekście Wyświetl warstwy (tekst, karetki i wyboru).  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("CommentAdornmentLayer")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition commentLayerDefinition;  
  
    ```  
  
## <a name="provide-comment-adornments"></a>Podaj zakończeń komentarz  
 Podczas definiowania zakończeń także implementować dostawcy zakończeń komentarz i Menedżera zakończeń komentarz. Dostawca zakończeń komentarz przechowuje listę zakończeń komentarza, nasłuchuje <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzenia bazowego bufor tekstowy i usuwa komentarz zakończeń, gdy tekst źródłowy zostanie usunięty.  
  
1.  Dodaj nowy plik klasy do projektu CommentAdornmentTest i nadaj mu nazwę `CommentAdornmentProvider`.  
  
2.  Dodaj następujący kod `using` instrukcji.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Collections.ObjectModel;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    ```  
  
3.  Dodaj klasę o nazwie `CommentAdornmentProvider`.  
  
    ```csharp  
    internal class CommentAdornmentProvider  
    {  
    }  
    ```  
  
4.  Dodaj pola prywatne w buforze tekstu i lista zakończeń komentarz związane z buforu.  
  
    ```csharp  
    private ITextBuffer buffer;  
    private IList<CommentAdornment> comments = new List<CommentAdornment>();  
  
    ```  
  
5.  Dodaj Konstruktor do `CommentAdornmentProvider`. Ten konstruktor powinien mieć dostęp prywatny, ponieważ dostawca jest tworzone przez `Create()` metody. Dodaje konstruktora `OnBufferChanged` procedurę obsługi zdarzeń do <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzeń.  
  
    ```csharp  
    private CommentAdornmentProvider(ITextBuffer buffer)  
    {  
        this.buffer = buffer;  
        //listen to the Changed event so we can react to deletions.   
        this.buffer.Changed += OnBufferChanged;  
    }  
  
    ```  
  
6.  Dodaj `Create()` metody.  
  
    ```csharp  
    public static CommentAdornmentProvider Create(IWpfTextView view)  
    {  
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });  
    }  
  
    ```  
  
7.  Dodaj `Detach()` metody.  
  
    ```csharp  
    public void Detach()  
    {  
        if (this.buffer != null)  
        {  
            //remove the Changed listener   
            this.buffer.Changed -= OnBufferChanged;  
            this.buffer = null;  
        }  
    }  
    ```  
  
8.  Dodaj `OnBufferChanged` programu obsługi zdarzeń.  
  
     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]  
  
9. Dodaj deklarację dla `CommentsChanged` zdarzeń.  
  
    ```csharp  
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;  
    ```  
  
10. Utwórz `Add()` metody w celu dodania zakończeń.  
  
    ```csharp  
    public void Add(SnapshotSpan span, string author, string text)  
    {  
        if (span.Length == 0)  
            throw new ArgumentOutOfRangeException("span");  
        if (author == null)  
            throw new ArgumentNullException("author");  
        if (text == null)  
            throw new ArgumentNullException("text");  
  
        //Create a comment adornment given the span, author and text.  
        CommentAdornment comment = new CommentAdornment(span, author, text);  
  
        //Add it to the list of comments.   
        this.comments.Add(comment);  
  
        //Raise the changed event.  
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;  
        if (commentsChanged != null)  
            commentsChanged(this, new CommentsChangedEventArgs(comment, null));  
    }  
  
    ```  
  
11. Dodaj `RemoveComments()` metody.  
  
    ```csharp  
    public void RemoveComments(SnapshotSpan span)  
    {  
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;  
  
        //Get a list of all the comments that are being kept   
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);  
  
        foreach (CommentAdornment comment in this.comments)  
        {  
            //find out if the given span overlaps with the comment text span. If two spans are adjacent, they do not overlap. To consider adjacent spans, use IntersectsWith.   
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))  
            {  
                //Raise the change event to delete this comment.   
                if (commentsChanged != null)  
                    commentsChanged(this, new CommentsChangedEventArgs(null, comment));  
            }  
            else  
                keptComments.Add(comment);  
        }  
  
        this.comments = keptComments;  
    }  
    ```  
  
12. Dodaj `GetComments()` metodę zwracającą wszystkie komentarze w zakresie danej migawki.  
  
    ```csharp  
    public Collection<CommentAdornment> GetComments(SnapshotSpan span)  
    {  
        IList<CommentAdornment> overlappingComments = new List<CommentAdornment>();  
        foreach (CommentAdornment comment in this.comments)  
        {  
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))  
                overlappingComments.Add(comment);  
        }  
  
        return new Collection<CommentAdornment>(overlappingComments);  
    }  
    ```  
  
13. Dodaj klasę o nazwie `CommentsChangedEventArgs`, wykonując następujące czynności.  
  
    ```csharp  
    internal class CommentsChangedEventArgs : EventArgs  
    {  
        public readonly CommentAdornment CommentAdded;  
  
        public readonly CommentAdornment CommentRemoved;  
  
        public CommentsChangedEventArgs(CommentAdornment added, CommentAdornment removed)  
        {  
            this.CommentAdded = added;  
            this.CommentRemoved = removed;  
        }  
    }  
    ```  
  
## <a name="manage-comment-adornments"></a>Zarządzanie zakończeń komentarz  
 Menedżer zakończeń komentarza tworzy zakończeń i dodaje go do warstwy zakończeń. Nasłuchuje on <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> i <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> zdarzenia, tak że można przenieść lub usunąć zakończeń. Nasłuchuje on również do `CommentsChanged` zdarzenia, które jest uruchamiane przez dostawcę zakończeń komentarza, gdy komentarze są dodawane lub usuwane.  
  
1.  Dodaj plik klasy do projektu CommentAdornmentTest i nadaj mu nazwę `CommentAdornmentManager`.  
  
2.  Dodaj następujący kod `using` instrukcji.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Windows.Media;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Formatting;  
    ```  
  
3.  Dodaj klasę o nazwie `CommentAdornmentManager`.  
  
    ```csharp  
    internal class CommentAdornmentManager  
        {  
        }  
    ```  
  
4.  Dodaj kilka pól prywatnych.  
  
    ```csharp  
    private readonly IWpfTextView view;  
    private readonly IAdornmentLayer layer;  
    private readonly CommentAdornmentProvider provider;  
    ```  
  
5.  Dodaj Konstruktor, który subskrybuje Menedżera <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> i <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> zdarzenia, a także `CommentsChanged` zdarzeń. Konstruktor nie jest prywatny, ponieważ Menedżer jest tworzone przez statyczną `Create()` metody.  
  
    ```csharp  
    private CommentAdornmentManager(IWpfTextView view)  
    {  
        this.view = view;  
        this.view.LayoutChanged += OnLayoutChanged;  
        this.view.Closed += OnClosed;  
  
        this.layer = view.GetAdornmentLayer("CommentAdornmentLayer");  
  
        this.provider = CommentAdornmentProvider.Create(view);  
        this.provider.CommentsChanged += OnCommentsChanged;  
    }  
    ```  
  
6.  Dodaj `Create()` metody, która pobiera dostawcy lub co powoduje utworzenie, jeśli to konieczne.  
  
    ```csharp  
    public static CommentAdornmentManager Create(IWpfTextView view)  
    {  
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });  
    }  
    ```  
  
7.  Dodaj `CommentsChanged` programu obsługi.  
  
    ```csharp  
    private void OnCommentsChanged(object sender, CommentsChangedEventArgs e)  
    {  
        //Remove the comment (when the adornment was added, the comment adornment was used as the tag).   
        if (e.CommentRemoved != null)  
            this.layer.RemoveAdornmentsByTag(e.CommentRemoved);  
  
        //Draw the newly added comment (this will appear immediately: the view does not need to do a layout).   
        if (e.CommentAdded != null)  
            this.DrawComment(e.CommentAdded);  
    }  
    ```  
  
8.  Dodaj <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> programu obsługi.  
  
    ```csharp  
    private void OnClosed(object sender, EventArgs e)  
    {  
        this.provider.Detach();  
        this.view.LayoutChanged -= OnLayoutChanged;  
        this.view.Closed -= OnClosed;  
    }  
    ```  
  
9. Dodaj <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> programu obsługi.  
  
    ```csharp  
    private void OnLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)  
    {  
        //Get all of the comments that intersect any of the new or reformatted lines of text.  
        List<CommentAdornment> newComments = new List<CommentAdornment>();  
  
        //The event args contain a list of modified lines and a NormalizedSpanCollection of the spans of the modified lines.    
        //Use the latter to find the comments that intersect the new or reformatted lines of text.   
        foreach (Span span in e.NewOrReformattedSpans)  
        {  
            newComments.AddRange(this.provider.GetComments(new SnapshotSpan(this.view.TextSnapshot, span)));  
        }  
  
        //It is possible to get duplicates in this list if a comment spanned 3 lines, and the first and last lines were modified but the middle line was not.   
        //Sort the list and skip duplicates.  
        newComments.Sort(delegate(CommentAdornment a, CommentAdornment b) { return a.GetHashCode().CompareTo(b.GetHashCode()); });  
  
        CommentAdornment lastComment = null;  
        foreach (CommentAdornment comment in newComments)  
        {  
            if (comment != lastComment)  
            {  
                lastComment = comment;  
                this.DrawComment(comment);  
            }  
        }  
    }  
    ```  
  
10. Dodaj metody prywatnej, który rysuje komentarz.  
  
     [!code-csharp[VSSDKMenuCommandTest#35](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs)]
     [!code-vb[VSSDKMenuCommandTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]  
  
## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>Użyj polecenia menu, aby dodać zakończeń komentarz  
 To polecenie umożliwia tworzenie zakończeń komentarz poprzez implementację `MenuItemCallback` metoda pakietu VSPackage.  
  
1.  Dodaj następujące odwołania do projektu MenuCommandTest:  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.Editor  
  
    -   Microsoft.VisualStudio.Text.UI.Wpf  
  
2.  Otwórz *AddAdornment.cs* pliku i Dodaj następujący kod `using` instrukcji.  
  
    ```csharp  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Editor;  
    using CommentAdornmentTest;  
    ```  
  
3.  Usuń `Execute()` metody i Dodaj następujący program obsługi poleceń.  
  
    ```csharp  
    private async void AddAdornmentHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
4.  Dodaj kod, aby uzyskać widok aktywny. Należy uzyskać `SVsTextManager` powłoki programu Visual Studio można pobrać aktywnej `IVsTextView`.  
  
    ```csharp  
    private async void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));  
        IVsTextView vTextView = null;  
        int mustHaveFocus = 1;  
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);  
    }  
    ```  
  
5.  Ten widok tekstu w przypadku wystąpienia widoku edytora tekstu, należy rzutować go na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> interfejsu, a następnie <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> i jego skojarzone <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>. Użyj <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> do wywołania `Connector.Execute()` metody, która pobiera dostawcę zakończeń komentarz, a następnie dodaje zakończeń. Program obsługi poleceń powinna teraz wyglądać podobnie do tego kodu:  
  
    ```csharp  
    private async void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));  
        IVsTextView vTextView = null;  
        int mustHaveFocus = 1;  
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);  
        IVsUserData userData = vTextView as IVsUserData;  
         if (userData == null)  
        {  
            Console.WriteLine("No text view is currently open");  
            return;  
        }  
        IWpfTextViewHost viewHost;  
        object holder;  
        Guid guidViewHost = DefGuidList.guidIWpfTextViewHost;  
        userData.GetData(ref guidViewHost, out holder);  
        viewHost = (IWpfTextViewHost)holder;  
        Connector.Execute(viewHost);  
    }  
    ```  
  
6.  Ustaw metodę AddAdornmentHandler jako procedura obsługi polecenia AddAdornment w Konstruktorze AddAdornment.  
  
    ```csharp  
    private AddAdornment(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        var menuCommandID = new CommandID(CommandSet, CommandId);
        var menuItem = new MenuCommand(this.AddAdornmentHandler, menuCommandID);
        commandService.AddCommand(menuItem);
    } 
    ```  
  
## <a name="build-and-test-the-code"></a>Tworzenie i testowanie kodu  
  
1.  Skompiluj rozwiązanie, a następnie rozpocząć debugowanie. Wystąpienie eksperymentalne powinna zostać wyświetlona.  
  
2.  Utwórz plik tekstowy. Wpisz jakiś tekst, a następnie wybierz ją.  
  
3.  Na **narzędzia** menu, kliknij przycisk **wywołania Dodaj zakończeń**. Dymek powinna zostać wyświetlona po prawej stronie okna tekstowego i może zawierać tekst, który przypomina następujący tekst.  
  
     Nazwa_użytkownika  
  
     Fourscore...  
  
## <a name="see-also"></a>Zobacz także  
 [Przewodnik: Połączyć typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
