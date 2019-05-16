---
title: 'Instrukcje: Dostęp do wbudowanych czcionek i schemat kolorów | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685308"
---
# <a name="how-to-access-the-built-in-fonts-and-color-scheme"></a>Instrukcje: Dostęp do wbudowanych czcionek i schemat kolorów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio zintegrowane środowisko programistyczne (IDE) zawiera schemat kolorów i czcionek, który jest skojarzony z oknem edytora. Możesz uzyskać dostęp za pośrednictwem systemu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejsu.  
  
 Aby korzystać z wbudowanych czcionek i kolorów schematu, pakietu VSPackage musi:  
  
- Definiowanie kategorii do użycia z usługą czcionki i kolory domyślne.  
  
- Zarejestruj kategorii z domyślnego serwera czcionek i kolorów.  
  
- Poinformowania środowiska IDE, że określone okno używa wbudowanego wyświetle elementy i kategorie za pomocą `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` i `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` interfejsów.  
  
  IDE używa wynikowej kategorii, jak dojścia do okna. Nazwa kategorii jest wyświetlana w **Pokaż ustawienia dla:** pole listy rozwijanej w **czcionki i kolory** stronę właściwości.  
  
### <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>Aby zdefiniować kategorii przy użyciu wbudowanych czcionki i kolory  
  
1. Utwórz dowolnego identyfikatora GUID.  
  
    Ten identyfikator GUID jest używany do jednoznacznego identyfikowania kategorii<strong>.</strong> Ta kategoria ponownie używa środowiska IDE domyślnej czcionki i kolory specyfikacji.  
  
   > [!NOTE]
   > Podczas pobierania danych czcionek i kolorów, za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> lub innych interfejsów pakietów VSPackage za pomocą tego identyfikatora GUID wbudowane informacje referencyjne.  
  
2. Nazwa kategorii należy dodać do tabeli ciągów wewnątrz pakietu VSPackage plik zasobów (.rc), dzięki czemu może być lokalizowana w razie potrzeby wyświetlane w środowisku IDE.  
  
    Aby uzyskać więcej informacji, zobacz [Dodawanie lub usuwanie ciągu](https://msdn.microsoft.com/library/077077b4-0f4b-4633-92d6-60b321164cab).  
  
### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>Aby zarejestrować kategorii przy użyciu wbudowanych czcionki i kolory  
  
1. Utworzyć specjalny typ wpisu rejestru kategorii w następującej lokalizacji:  
  
     [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio version>* \FontAndColors\\*\<Category>*]  
  
     *\<Kategoria >* to niezlokalizowana nazwa kategorii.  
  
2. Należy wypełnić rejestru podstawowe czcionek i kolorów schematu za pomocą czterech wartości:  
  
    |Nazwa|Typ|Dane|Opis|  
    |----------|----------|----------|-----------------|  
    |Kategoria|REG_SZ|Identyfikator GUID|Dowolny identyfikator GUID, który identyfikuje kategorii, który zawiera podstawowe schematu czcionek i kolorów.|  
    |Package|REG_SZ|Identyfikator GUID|{F5E7E71D-1401-11D1-883B-0000F87579D2}<br /><br /> Ten identyfikator GUID jest używana przez wszystkich pakietów VSPackage, korzystających z domyślnymi konfiguracjami czcionek i kolorów.|  
    |NameID|REG_DWORD|Identyfikator|Identyfikator zasobu Nazwa kategorii możliwych do zlokalizowania w pakietu VSPackage.|  
    |ToolWindowPackage|REG_SZ|Identyfikator GUID|Identyfikator GUID pakietu VSPackage wykonawczych <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejsu.|  
  
3. 
  
### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>Aby zainicjować użycie dostarczane przez system czcionek i kolorów  
  
1. Utwórz wystąpienie obiektu `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` interfejsu jako część wdrożenia i Inicjowanie okna.  
  
2. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> metodę, aby uzyskać wystąpienia `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` interfejsu odpowiadającą bieżącej <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> wystąpienia.  
  
3. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> dwa razy.  
  
   - Wywołaj raz za pomocą `VSEDITPROPID_ViewGeneral_ColorCategory`jako argument.  
  
   - Wywołaj raz za pomocą `VSEDITPROPID_ViewGeneral_FontCategory` jako argument.  
  
     Spowoduje to i udostępnia usługi czcionki i kolory domyślne jako właściwość okna.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład powoduje zainicjowanie użycie wbudowanych czcionek i kolorów.  
  
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
 [Wprowadzenie czcionkę i kolor informacje dotyczące kolorowania tekstu](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Uzyskiwanie dostępu do przechowywanych czcionkę i kolor ustawienia](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Omówienie czcionek i kolorów](../extensibility/font-and-color-overview.md)
