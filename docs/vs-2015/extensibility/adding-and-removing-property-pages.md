---
title: Dodawanie i usuwanie stron właściwości | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- property pages, adding
- property pages, project subtypes
- property pages, removing
ms.assetid: 34853412-ab8a-4caa-9601-7d0727b2985d
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 98838f09df3094e16d5f1a18263ffdad603ded0b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440138"
---
# <a name="adding-and-removing-property-pages"></a>Dodawanie i usuwanie stron właściwości
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W Projektancie projektu stanowi centralną lokalizację służącą do zarządzania właściwości projektu, ustawień i zasobów w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Będzie ono wyświetlane jako jednego okna w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zintegrowane środowisko projektowe (IDE) i zawiera szereg okienka po prawej stronie, które są dostępne za pośrednictwem na kartach po lewej stronie. Okienka (często określanymi jako strony właściwości) w Projektancie projektu zależą od typu projektu i język. W Projektancie projektu jest możliwy za pomocą **właściwości** polecenie **projektu** menu.  
  
 Często podtypu projektu musi wyświetlić dodatkowe strony właściwości w Projektancie projektu. Podobnie niektóre podtypy projektów mogą wymagać usunięcia wbudowanej właściwości strony. Albo celu usługi podtypu projektu musi implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfejs i zastąpić <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> metody. Zastąpienie tej metody, a za pomocą `propId` parametr zawierający jedną z wartości <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> wyliczania, można filtrować, dodawać lub usuwać właściwości projektu. Na przykład może być konieczne dodawanie strony do strony właściwości zależne od konfiguracji. Aby to zrobić, należy filtrować strony właściwości zależne od konfiguracji, a następnie dodaj nową stronę do istniejącej listy.  
  
## <a name="adding-and-removing-property-pages-in-project-designer"></a>Dodawanie i usuwanie stron właściwości w Projektancie projektu  
  
#### <a name="to-remove-a-property-page-in-project-designer"></a>Aby usunąć stronę właściwości w Projektancie projektu  
  
1. Zastąp `GetProperty(uint itemId, int propId, out object property)` metodę, aby filtrować strony właściwości i uzyskać `clsids` listy.  
  
    ```vb  
    Protected Overrides int GetProperty(uint itemId, int propId, out object property)  
    Protected Overrides Function GetProperty(ByVal itemId As UInteger, ByVal propId As Integer, ByRef [property] As Object) As Integer  
        'Use propId to filter configuration-independent property pages.  
        Select Case propId  
            ....   
            Case CInt(Fix(__VSHPROPID2.VSHPROPID_PropertyPagesCLSIDList))  
                'Get a semicolon-delimited list of clsids of the configuration-independent property pages  
                ErrorHandler.ThrowOnFailure(MyBase.GetProperty(itemId, propId, [property]))  
                   Dim propertyPagesList As String = ((String)[property]).ToUpper(CultureInfo.InvariantCulture)  
                'Remove the property page here  
                   ....  
            ....  
        End Select  
            ....   
        Return MyBase.GetProperty(itemId, propId, [property])  
    End Function  
  
    ```  
  
    ```csharp  
    protected override int GetProperty(uint itemId, int propId, out object property)  
    {  
        //Use propId to filter configuration-independent property pages.  
        switch (propId)  
        {  
            . . . .  
  
            case (int)__VSHPROPID2.VSHPROPID_PropertyPagesCLSIDList:  
                {  
                    //Get a semicolon-delimited list of clsids of the configuration-independent property pages  
                    ErrorHandler.ThrowOnFailure(base.GetProperty(itemId, propId, out property));  
                    string propertyPagesList = ((string)property).ToUpper(CultureInfo.InvariantCulture);  
                    //Remove the property page here  
                    . . . .  
                }  
             . . . .  
         }  
            . . . .  
        return base.GetProperty(itemId, propId, out property);  
    }  
    ```  
  
2. Usuń **zdarzenia kompilacji** uzyskane strony `clsids` listy.  
  
    ```vb  
    Private buildEventsPageGuid As String = "{1E78F8DB-6C07-4D61-A18F-7514010ABD56}"  
    Private index As Integer = propertyPagesList.IndexOf(buildEventsPageGuid)  
    If index <> -1 Then  
        ' GUIDs are separated by ';' so if you remove the last GUID, also remove the last ';'  
        Dim index2 As Integer = index + buildEventsPageGuid.Length + 1  
        If index2 >= propertyPagesList.Length Then  
            propertyPagesList = propertyPagesList.Substring(0, index).TrimEnd(";"c)  
        Else  
            propertyPagesList = propertyPagesList.Substring(0, index) + propertyPagesList.Substring(index2)  
        End If  
    End If  
    'New property value  
    property = propertyPagesList  
    ```  
  
    ```csharp  
    string buildEventsPageGuid = "{1E78F8DB-6C07-4D61-A18F-7514010ABD56}";  
    int index = propertyPagesList.IndexOf(buildEventsPageGuid);  
    if (index != -1)  
    {  
        // GUIDs are separated by ';' so if you remove the last GUID, also remove the last ';'  
        int index2 = index + buildEventsPageGuid.Length + 1;  
        if (index2 >= propertyPagesList.Length)  
            propertyPagesList = propertyPagesList.Substring(0, index).TrimEnd(';');  
        else  
            propertyPagesList = propertyPagesList.Substring(0, index) + propertyPagesList.Substring(index2);  
    }  
    //New property value  
    property = propertyPagesList;  
    ```  
  
#### <a name="to-add-a-property-page-in-project-designer"></a>Aby dodać stronę właściwości w Projektancie projektu  
  
1. Utwórz stronę właściwości, które chcesz dodać.  
  
    ```vb  
    Class DeployPropertyPage  
            Inherits Form  
            Implements Microsoft.VisualStudio.OLE.Interop.IPropertyPage  
        'Summary: Return a stucture describing your property page.  
        ....   
        Public Sub GetPageInfo(ByVal pPageInfo As Microsoft.VisualStudio.OLE.Interop.PROPPAGEINFO())  
            Dim info As PROPPAGEINFO = New PROPPAGEINFO()  
            info.cb = CUInt(Marshal.SizeOf(GetType(PROPPAGEINFO)))  
            info.dwHelpContext = 0  
            info.pszDocString = Nothing  
            info.pszHelpFile = Nothing  
            info.pszTitle = "Deployment" 'Assign tab name  
            info.SIZE.cx = Me.Size.Width  
            info.SIZE.cy = Me.Size.Height  
            If Not pPageInfo Is Nothing AndAlso pPageInfo.Length > 0 Then  
                pPageInfo(0) = info  
            End If  
        End Sub  
    End Class  
    ```  
  
    ```csharp  
    class DeployPropertyPage : Form, Microsoft.VisualStudio.OLE.Interop.IPropertyPage  
    {  
        . . . .   
        //Summary: Return a stucture describing your property page.  
        public void GetPageInfo(Microsoft.VisualStudio.OLE.Interop.PROPPAGEINFO[] pPageInfo)  
        {  
            PROPPAGEINFO info = new PROPPAGEINFO();  
            info.cb = (uint)Marshal.SizeOf(typeof(PROPPAGEINFO));  
            info.dwHelpContext = 0;  
            info.pszDocString = null;  
            info.pszHelpFile = null;  
            info.pszTitle = "Deployment";  //Assign tab name  
            info.SIZE.cx = this.Size.Width;  
            info.SIZE.cy = this.Size.Height;  
            if (pPageInfo != null && pPageInfo.Length > 0)  
                pPageInfo[0] = info;  
        }  
    }  
    ```  
  
2. Zarejestruj swoje nowe strony właściwości.  
  
    ```vb  
    <MSVSIP.ProvideObject(GetType(DeployPropertyPage), RegisterUsing = RegistrationMethod.CodeBase)>  
    ```  
  
    ```csharp  
    [MSVSIP.ProvideObject(typeof(DeployPropertyPage), RegisterUsing = RegistrationMethod.CodeBase)]  
    ```  
  
3. Zastąp `GetProperty(uint itemId, int propId, out object property)` metodę, aby filtrować strony właściwości, Uzyskaj `clsids` listy i Dodaj nową stronę właściwości.  
  
    ```vb  
    Protected Overrides Function GetProperty(ByVal itemId As UInteger, ByVal propId As Integer, ByRef [property] As Object) As Integer  
        'Use propId to filter configuration-dependent property pages.  
        Select Case propId  
            ....   
            case CInt(Fix(__VSHPROPID2.VSHPROPID_CfgPropertyPagesCLSIDList)):  
                'Get a semicolon-delimited list of clsids of the configuration-dependent property pages.  
                ErrorHandler.ThrowOnFailure(MyBase.GetProperty(itemId, propId, [property]))  
                'Add the Deployment property page.  
                [property] &= ";"c + GetType(DeployPropertyPage).GUID.ToString("B")  
        End Select  
            ....   
            Return MyBase.GetProperty(itemId, propId, [property])  
    End Function  
    ```  
  
    ```csharp  
    protected override int GetProperty(uint itemId, int propId, out object property)  
    {  
        //Use propId to filter configuration-dependent property pages.  
        switch (propId)  
        {  
            . . . .  
            case (int)__VSHPROPID2.VSHPROPID_CfgPropertyPagesCLSIDList:  
                {  
                    //Get a semicolon-delimited list of clsids of the configuration-dependent property pages.  
                    ErrorHandler.ThrowOnFailure(base.GetProperty(itemId, propId, out property));  
                    //Add the Deployment property page.  
                    property += ';' + typeof(DeployPropertyPage).GUID.ToString("B");  
                }  
         }  
            . . . .  
        return base.GetProperty(itemId, propId, out property);  
    }  
    ```  
  
> [!NOTE]
> Wszystkie przykłady kodu, podane w tym temacie stanowią część większego przykładu [przykłady VSSDK](../misc/vssdk-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Podtypy projektów](../extensibility/internals/project-subtypes.md)
