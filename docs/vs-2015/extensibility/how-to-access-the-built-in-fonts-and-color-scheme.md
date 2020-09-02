---
title: 'Instrukcje: uzyskiwanie dostępu do wbudowanych czcionek i schematu kolorów | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a43fb3a22ecb2d04542eacf07bf883590868b75b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685308"
---
# <a name="how-to-access-the-built-in-fonts-and-color-scheme"></a>Instrukcje: uzyskiwanie dostępu do wbudowanych czcionek i schematu kolorów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zintegrowane środowisko programistyczne (IDE) programu Visual Studio zawiera schemat czcionek i kolorów, które są skojarzone z oknem edytora. Dostęp do tego schematu można uzyskać za pomocą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejsu.  
  
 Aby użyć wbudowanego schematu czcionek i kolorów, pakietu VSPackage musi:  
  
- Zdefiniuj kategorię do użycia z domyślną czcionką i kolorami.  
  
- Zarejestruj kategorię z domyślnymi czcionkami i kolorami.  
  
- Należy polecić IDE, aby określone okno używało wbudowanych elementów i kategorii wyświetlanych za pomocą `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` interfejsów i `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` .  
  
  IDE używa uzyskanej kategorii jako uchwytu do okna. Nazwa kategorii zostanie wyświetlona w polu listy rozwijanej **Pokaż ustawienia dla:** na stronie właściwości **czcionki i kolory** .  
  
### <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>Aby zdefiniować kategorię przy użyciu wbudowanych czcionek i kolorów  
  
1. Utwórz dowolny identyfikator GUID.  
  
    Ten identyfikator GUID służy do jednoznacznego identyfikowania kategorii<strong>.</strong> Ta kategoria ponownie używa domyślnych ustawień czcionek i kolorów IDE.  
  
   > [!NOTE]
   > Podczas pobierania danych czcionki i koloru przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> lub innych interfejsów pakietów VSPackage Użyj tego identyfikatora GUID, aby odwołać się do wbudowanych informacji.  
  
2. Nazwa kategorii musi być dodana do tabeli ciągów wewnątrz pliku zasobów pakietu VSPackage (. RC), dzięki czemu może być lokalizowana w razie potrzeby, gdy jest wyświetlana w IDE.  
  
    Aby uzyskać więcej informacji, zobacz [Dodawanie lub usuwanie ciągu](https://msdn.microsoft.com/library/077077b4-0f4b-4633-92d6-60b321164cab).  
  
### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>Aby zarejestrować kategorię przy użyciu wbudowanych czcionek i kolorów  
  
1. Utwórz specjalny typ wpisu rejestru kategorii w następującej lokalizacji:  
  
     [HKLM\SOFTWARE\Microsoft \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ *\<Category>* ]  
  
     *\<Category>* to niezlokalizowana nazwa kategorii.  
  
2. Wypełnij rejestr, aby użyć czcionek i schematu kolorów z czterema wartościami:  
  
    |Nazwa|Typ|Dane|Opis|  
    |----------|----------|----------|-----------------|  
    |Kategoria|REG_SZ|GUID|Dowolny identyfikator GUID, który identyfikuje kategorię zawierającą czcionkę i schemat kolorów.|  
    |Pakiet|REG_SZ|GUID|{F5E7E71D-1401-11D1-883B-0000F87579D2}<br /><br /> Ten identyfikator GUID jest używany przez wszystkie pakietów VSPackage, które używają domyślnych konfiguracji czcionek i kolorów.|  
    |NameID|REG_DWORD|ID|Identyfikator zasobu lokalizowalnej nazwy kategorii w pakietu VSPackage.|  
    |ToolWindowPackage|REG_SZ|GUID|Identyfikator GUID pakietu VSPackage implementującej <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejs.|  
  
3. 
  
### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>Aby zainicjować korzystanie z czcionek i kolorów dostarczonych przez system  
  
1. Utwórz wystąpienie `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` interfejsu w ramach implementacji i inicjalizacji okna.  
  
2. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> metodę, aby uzyskać wystąpienie `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` interfejsu odpowiadającego bieżącemu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> wystąpieniu.  
  
3. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> dwa razy.  
  
   - Wywołaj raz z `VSEDITPROPID_ViewGeneral_ColorCategory` argumentem.  
  
   - Wywołaj raz z `VSEDITPROPID_ViewGeneral_FontCategory` argumentem.  
  
     Powoduje to skonfigurowanie i uwidocznienie domyślnych czcionek i usług kolorów jako właściwości okna.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład inicjuje użycie wbudowanych czcionek i kolorów.  
  
```  
CComVariant vt;  
CComQIPtr<IVsTextEditorPropertyCategoryContainer> spPropCatContainer(m_spView);  
if (spPropCatContainer != NULL){  
    CComPtr<IVsTextEditorPropertyContainer> spPropContainer;  
    if (SUCCEEDED(spPropCatContainer->GetPropertyCategory(GUID_EditPropCategory_View_MasterSettings,   
                                                          &spPropContainer))){  
        CComVariant vt;CComVariant VariantGUID(bstrGuidText);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_FontCategory, VariantGUID);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_ColorCategory, VariantGUID);  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie czcionek i kolorów](../extensibility/using-fonts-and-colors.md)   
 [Uzyskiwanie informacji o czcionkach i kolorach na potrzeby kolorowania tekstu](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Uzyskiwanie dostępu do przechowywanych ustawień czcionek i kolorów](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Omówienie czcionek i kolorów](../extensibility/font-and-color-overview.md)
