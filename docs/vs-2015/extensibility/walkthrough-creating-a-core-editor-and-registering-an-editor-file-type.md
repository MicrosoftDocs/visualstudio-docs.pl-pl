---
title: 'Przewodnik: Tworzenie podstawowego edytora i rejestrowanie typu pliku edytora | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 14296aa335ba6710d4d9eac8e5338af7463c0aac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687633"
---
# <a name="walkthrough-creating-a-core-editor-and-registering-an-editor-file-type"></a>Przewodnik: tworzenie edytora podstawowego i rejestrowanie typu pliku edytora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu przedstawiono sposób tworzenia pakietu VSPackage, który uruchamia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Edytor podstawowy, gdy plik z rozszerzeniem nazwy pliku. myext jest ładowany.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby wykonać czynności opisane w tym przewodniku, należy zainstalować Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Lokalizacje szablonu projektu pakietu programu Visual Studio  
 Szablon projektu pakietu programu Visual Studio można znaleźć w trzech różnych lokalizacjach w oknie dialogowym **Nowy projekt** :  
  
1. W obszarze rozszerzalność Visual Basic. Domyślny język projektu jest Visual Basic.  
  
2. W obszarze rozszerzalność języka C#. Językiem domyślnym projektu jest C#.  
  
3. W obszarze Inne typy rozszerzeń projektu. Językiem domyślnym projektu jest C++.  
  
### <a name="to-create-the-vspackage"></a>Aby utworzyć pakietu VSPackage  
  
- Uruchom [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i Utwórz [!INCLUDE[csprcs](../includes/csprcs-md.md)] pakietu VSPackage o nazwie `MyPackage` , jak opisano w [przewodniku: Tworzenie polecenia menu pakietu VSPackage](https://msdn.microsoft.com/d699c149-5d1e-47ff-94c7-e1222af02c32).  
  
### <a name="to-add-the-editor-factory"></a>Aby dodać fabrykę edytora  
  
1. Kliknij prawym przyciskiem myszy projekt moje **Package** , wskaż polecenie **Dodaj** , a następnie kliknij pozycję **Klasa**.  
  
2. W oknie dialogowym **Dodaj nowy element** upewnij się, że jest wybrana pozycja szablon **klasy** , wpisz `EditorFactory.cs` nazwę, a następnie kliknij przycisk **Dodaj** , aby dodać klasę do projektu.  
  
     Plik EditorFactory.cs powinien zostać otwarty automatycznie.  
  
3. Odwołuje się do następujących zestawów z kodu.  
  
    ```vb  
    Imports System.Runtime.InteropServices  
    Imports Microsoft.VisualStudio  
    Imports Microsoft.VisualStudio.Shell  
    Imports Microsoft.VisualStudio.Shell.Interop  
    Imports Microsoft.VisualStudio.OLE.Interop  
    Imports Microsoft.VisualStudio.TextManager.Interop  
    Imports IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider  
    ```  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
  
    ```  
  
4. Dodaj identyfikator GUID do `EditorFactory` klasy, dodając `Guid` atrybut bezpośrednio przed deklaracją klasy.  
  
     Nowy identyfikator GUID można wygenerować za pomocą programu guidgen.exe w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wierszu polecenia lub klikając polecenie **Utwórz GUID** w menu **Narzędzia** . Identyfikator GUID używany tutaj jest tylko przykładem; nie należy używać go w projekcie.  
  
    ```vb  
    <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _  
    ```  
  
    ```csharp  
    [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]   
    ```  
  
5. W definicji klasy Dodaj dwie zmienne prywatne, aby zawierały pakiet nadrzędny i dostawcę usług.  
  
    ```vb  
    Class EditorFactory  
        Private parentPackage As Package  
        Private serviceProvider As IOleServiceProvider  
    ```  
  
    ```csharp  
    class EditorFactory  
    {  
        private Package parentPackage;  
        private IOleServiceProvider serviceProvider;  
    }  
  
    ```  
  
6. Dodaj Konstruktor klasy publicznej, który przyjmuje jeden parametr typu <xref:Microsoft.VisualStudio.Shell.Package> :  
  
    ```vb  
    Public Sub New(ByVal parentPackage As Package)  
        Me.parentPackage = parentPackage  
    End Sub  
    ```  
  
    ```csharp  
    public EditorFactory(Package parentPackage)  
    {  
        this.parentPackage = parentPackage;  
    }  
    ```  
  
7. Zmodyfikuj `EditorFactory` deklarację klasy, aby dziedziczyć z <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfejsu.  
  
    ```vb  
    Class EditorFactory Implements IVsEditorFacto  
    ```  
  
    ```csharp  
    class EditorFactory : IVsEditorFactory  
  
    ```  
  
8. Kliknij prawym przyciskiem myszy <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> , kliknij pozycję **Implementuj interfejs**, a następnie kliknij pozycję **Implementuj interfejs jawnie**.  
  
     Spowoduje to dodanie czterech metod, które muszą być zaimplementowane w <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfejsie.  
  
9. Zastąp zawartość metody `IVsEditorFactory.Close` następującym kodem.  
  
    ```vb  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
10. Zastąp zawartość `IVsEditorFactory.SetSite` następującym kodem.  
  
    ```vb  
    Me.serviceProvider = psp  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    this.serviceProvider = psp;  
    return VSConstants.S_OK;  
    ```  
  
11. Zastąp zawartość metody `IVsEditorFactory.MapLogicalView` następującym kodem.  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_NOTIMPL  
    pbstrPhysicalView = Nothing ' We support only one view.  
    If rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer)OrElse _  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary) Then  
        retval = VSConstants.S_OK  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_NOTIMPL;  
    pbstrPhysicalView = null;   // We support only one view.  
    if (rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer) ||  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary))  
    {  
        retval = VSConstants.S_OK;  
    }  
    return retval;  
    ```  
  
12. Zastąp zawartość metody `IVsEditorFactory.CreateEditorInstance` następującym kodem.  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_FAIL          
  
    ' Initialize these to empty to start with   
    ppunkDocView = IntPtr.Zero  
    ppunkDocData = IntPtr.Zero  
    pbstrEditorCaption = ""  
    pguidCmdUI = Guid.Empty  
    pgrfCDW = 0  
  
    If (grfCreateDoc And (VSConstants.CEF_OPENFILE Or _  
    VSConstants.CEF_SILENT)) = 0 Then  
        Throw New ArgumentException("Only Open or Silent is valid")  
    End If  
    If punkDocDataExisting <> IntPtr.Zero Then  
        Return VSConstants.VS_E_INCOMPATIBLEDOCDATA  
    End If  
  
    ' Instantiate a text buffer of type VsTextBuffer.   
    ' Note: we only need an IUnknown (object) interface for   
    ' this invocation.   
    Dim clsidTextBuffer As Guid = GetType(VsTextBufferClass).GUID  
    Dim iidTextBuffer As Guid = VSConstants.IID_IUnknown  
    Dim pTextBuffer As Object = pTextBuffer = _  
    parentPackage.CreateInstance(clsidTextBuffer, iidTextBuffer, _  
    GetType(Object))  
  
    If Not pTextBuffer Is Nothing Then  
        ' "Site" the text buffer with the service provider we were   
        ' provided.   
        Dim textBufferSite As IObjectWithSite = TryCast(pTextBuffer, _  
        IObjectWithSite)  
        If Not textBufferSite Is Nothing Then  
            textBufferSite.SetSite(Me.serviceProvider)  
        End If  
  
        ' Instantiate a code window of type IVsCodeWindow.   
        Dim clsidCodeWindow As Guid = GetType(VsCodeWindowClass).GUID  
        Dim iidCodeWindow As Guid = GetType(IVsCodeWindow).GUID  
        Dim pCodeWindow As IVsCodeWindow = _  
        CType(Me.parentPackage.CreateInstance(clsidCodeWindow, _  
        iidCodeWindow, GetType(IVsCodeWindow)), IVsCodeWindow)  
        If Not pCodeWindow Is Nothing Then  
            ' Give the text buffer to the code window.   
            ' We are giving up ownership of the text buffer!   
            pCodeWindow.SetBuffer(CType(pTextBuffer, IVsTextLines))  
  
            ' Now tell the caller about all this new stuff   
            ' that has been created.   
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow)  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer)  
  
            ' Specify the command UI to use so keypresses are   
            ' automatically dealt with.   
            pguidCmdUI = VSConstants.GUID_TextEditorFactory  
  
            ' This caption is appended to the filename and   
            ' lets us know our invocation of the core editor   
            ' is up and running.   
            pbstrEditorCaption = " [MyPackage]"  
  
            retval = VSConstants.S_OK  
        End If  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_FAIL;  
  
    // Initialize these to empty to start with  
    ppunkDocView       = IntPtr.Zero;  
    ppunkDocData       = IntPtr.Zero;  
    pbstrEditorCaption = "";  
    pguidCmdUI         = Guid.Empty;   
    pgrfCDW            = 0;  
  
    if ((grfCreateDoc & (VSConstants.CEF_OPENFILE |   
          VSConstants.CEF_SILENT)) == 0)  
    {   
        throw new ArgumentException("Only Open or Silent is valid");  
    }  
    if (punkDocDataExisting != IntPtr.Zero)  
    {  
        return VSConstants.VS_E_INCOMPATIBLEDOCDATA;  
    }  
  
    // Instantiate a text buffer of type VsTextBuffer.  
    // Note: we only need an IUnknown (object) interface for   
    // this invocation.  
    Guid clsidTextBuffer = typeof(VsTextBufferClass).GUID;  
    Guid iidTextBuffer   = VSConstants.IID_IUnknown;  
    object pTextBuffer   = pTextBuffer = parentPackage.CreateInstance(  
          ref clsidTextBuffer,  
          ref iidTextBuffer,  
          typeof(object));  
  
    if (pTextBuffer != null)  
    {  
        // "Site" the text buffer with the service provider we were  
        // provided.  
        IObjectWithSite textBufferSite = pTextBuffer as IObjectWithSite;  
        if (textBufferSite != null)  
        {  
            textBufferSite.SetSite(this.serviceProvider);  
        }  
  
        // Instantiate a code window of type IVsCodeWindow.  
        Guid clsidCodeWindow = typeof(VsCodeWindowClass).GUID;  
        Guid iidCodeWindow   = typeof(IVsCodeWindow).GUID;  
        IVsCodeWindow pCodeWindow =  
        (IVsCodeWindow)this.parentPackage.CreateInstance(   
              ref clsidCodeWindow,  
              ref iidCodeWindow,  
              typeof(IVsCodeWindow));  
        if (pCodeWindow != null)  
        {  
            // Give the text buffer to the code window.  
            // We are giving up ownership of the text buffer!  
            pCodeWindow.SetBuffer((IVsTextLines)pTextBuffer);  
  
            // Now tell the caller about all this new stuff   
            // that has been created.  
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow);  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer);  
  
            // Specify the command UI to use so keypresses are   
            // automatically dealt with.  
            pguidCmdUI = VSConstants.GUID_TextEditorFactory;  
  
            // This caption is appended to the filename and  
            // lets us know our invocation of the core editor   
            // is up and running.  
            pbstrEditorCaption = " [MyPackage]";  
  
            retval = VSConstants.S_OK;  
        }   
    }   
    return retval;   
    ```  
  
13. Skompiluj projekt i upewnij się, że nie ma żadnych błędów.  
  
### <a name="to-register-the-editor-factory"></a>Aby zarejestrować fabrykę edytora  
  
1. W **Eksplorator rozwiązań**kliknij dwukrotnie plik resources. resx, aby otworzyć go w tabeli ciągów, w której jest wybrany element **ciąg1** .  
  
2. Zmień nazwę identyfikatora na `IDS_EDITORNAME` i tekst do **edytora webpackage.** Ten ciąg będzie wyświetlany jako nazwa edytora.  
  
3. Otwórz plik pakietu VSPackage. resx i Dodaj nowy ciąg, Ustaw nazwę na **101** i wartość na `IDS_EDITORNAME` . Zapewnia to pakiet z IDENTYFIKATORem zasobu, aby uzyskać dostęp do właśnie utworzonego ciągu.  
  
    > [!NOTE]
    > Jeśli plik pakietu VSPackage. resx zawiera inny ciąg, który ma `name` atrybut ustawiony na **101**, należy zastąpić inną unikatową wartość liczbową w tym miejscu i w poniższych krokach.  
  
4. W **Eksplorator rozwiązań**otwórz plik MyPackagePackage.cs.  
  
     Jest to główny plik pakietu.  
  
5. Dodaj następujące atrybuty użytkownika tuż przed `Guid` atrybutem.  
  
    ```vb  
    <ProvideEditorFactoryAttribute(GetType(EditorFactory), 101)> _  
    <ProvideEditorExtensionAttribute(GetType(EditorFactory), _  
          ".myext", 32, NameResourceID:=101 )> _  
    ```  
  
    ```csharp  
    [ProvideEditorFactory(typeof(EditorFactory), 101)]  
    [ProvideEditorExtension(typeof(EditorFactory),   
          ".myext", 32, NameResourceID = 101)]   
    ```  
  
     Ten <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> atrybut kojarzy rozszerzenie pliku. myext z fabryką edytora, aby w dowolnym momencie załadować plik, który ma to rozszerzenie, fabryka edytora zostanie wywołana.  
  
6. Dodaj zmienną prywatną do `MyPackage` klasy, tuż przed konstruktorem, i nadaj jej typ `EditorFactory` .  
  
    ```vb  
    Private editorFactory As EditorFactory  
    ```  
  
    ```csharp  
    private EditorFactory editorFactory;  
    ```  
  
7. Znajdź `Initialize` metodę (może być konieczne otwarcie `Package Members` regionu ukrytego) i dodanie poniższego kodu po wywołaniu `base.Initialize()` .  
  
    ```vb  
    'Create our editor factory and register it.   
    Me.editorFactory = New EditorFactory(Me)  
    MyBase.RegisterEditorFactory(Me.editorFactory)  
    ```  
  
    ```csharp  
    // Create our editor factory and register it.  
    this.editorFactory = new EditorFactory(this);  
    base.RegisterEditorFactory(this.editorFactory);  
  
    ```  
  
8. Skompiluj program i upewnij się, że nie ma żadnych błędów.  
  
     W tym kroku zarejestrowano fabrykę edytora w ramach eksperymentalnej gałęzi rejestru dla programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Jeśli zostanie wyświetlony monit o zastąpienie pliku Resource. h, kliknij przycisk **OK**.  
  
9. Utwórz przykładowy plik o nazwie textplik1. myext.  
  
10. Naciśnij klawisz **F5** , aby otworzyć wystąpienie eksperymentalne [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
11. W obszarze eksperymentalne [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] w menu **plik** wskaż polecenie **Otwórz** , a następnie kliknij pozycję **plik**.  
  
12. Znajdź textplik1. myext, a następnie kliknij przycisk **Otwórz**.  
  
     Plik powinien być teraz załadowany.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Podstawowy edytor obsługuje szeroką gamę typów plików tekstowych i ściśle współpracuje z usługami językowymi, aby zapewnić bogaty zestaw funkcji, takich jak wyróżnianie składni, dopasowywanie nawiasów klamrowych i listy uzupełniania elementów członkowskich. Jeśli pracujesz z plikami tekstowymi, możesz użyć podstawowego edytora wraz z niestandardową usługą języka, która obsługuje określone typy plików.  
  
 Pakietu VSPackage może wywołać [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] podstawowy edytor, dostarczając fabrykę edytora. Ta fabryka edytora jest używana za każdym razem, gdy skojarzony z nim plik zostanie załadowany. Jeśli plik jest częścią projektu, podstawowy edytor jest automatycznie wywoływany, chyba że zostanie zastąpiony przez pakietu VSPackage. Jeśli jednak plik jest ładowany poza projektem, to podstawowy edytor musi być jawnie wywoływany przez pakietu VSPackage.  
  
 Aby uzyskać więcej informacji na temat podstawowego edytora, zobacz [w edytorze core](../extensibility/inside-the-core-editor.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wewnątrz edytora podstawowego](../extensibility/inside-the-core-editor.md)   
 [Tworzenie wystąpienia edytora podstawowego przy użyciu starszej wersji interfejsu API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)
