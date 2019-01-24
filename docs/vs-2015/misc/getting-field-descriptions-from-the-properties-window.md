---
title: Wprowadzenie opisy pól z okna właściwości | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Properties window, field descriptions
ms.assetid: 7d92bb6a-b9b9-4cd8-99e9-b5ee129b52a3
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 0fa07029ee1b96f3b8f1328d654b4d5d83953142
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54797220"
---
# <a name="getting-field-descriptions-from-the-properties-window"></a>Wprowadzenie opisy pól z okna właściwości
W dolnej części **właściwości** , obszar opisu wyświetlane są informacje związane z pól wybranych właściwości. Ta funkcja jest włączona domyślnie. Jeśli chcesz ukryć pole opisu, kliknij prawym przyciskiem myszy **właściwości** oknie i kliknij przycisk **opis**. Ten sposób spowoduje również usunięcie znacznik wyboru obok pozycji **opis** tytuł w oknie menu. Wyświetlanie pola ponownie, wykonując te same kroki, aby przełączyć **opis** ponownie.  
  
 Informacje w polu opisu pochodzą z <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Każda metoda, interfejsu, klasa coclass i tak dalej, może mieć Niezlokalizowany `helpstring` atrybutu w bibliotece typów. **Właściwości** okna pobiera ciąg, z <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>.  
  
### <a name="to-specify-localized-help-strings"></a>Aby określić parametry zlokalizowanej pomocy  
  
1. Dodaj `helpstringdll` atrybutu po instrukcji library w bibliotece typów (`typelib`).  
  
   > [!NOTE]
   >  Ten krok jest opcjonalny, jeśli biblioteka typów znajduje się w pliku biblioteki (.olb) obiektu.  
  
2. Określ `helpstringcontext` atrybuty dla ciągów. Można również określić `helpstring` atrybutów.  
  
    Te atrybuty różnią się od `helpfile` i `helpcontext` atrybuty, które znajdują się w tematach pomocy plik chm rzeczywistych.  
  
   Można pobrać informacji o opis ma być wyświetlany nazwę właściwości wyróżnione **właściwości** wywołania okna <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> dla właściwości, która jest zaznaczone, określając żądane `lcid` atrybutu dla Ciąg wyjściowy. Wewnętrznie <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> znajdzie plik .dll, określone w `helpstringdll` atrybutu i wywołania `DLLGetDocumentation` z tym plikiem dll, przy użyciu określonego kontekstu i `lcid` atrybutu.  
  
   Podpis i implementację `DLLGetDocumentation` są:  
  
```  
STDAPI DLLGetDocumentation  
(  
   ITypeLib * /* ptlib */,  
   ITypeInfo * /* ptinfo */,  
   LCID /* lcid */,  
   DWORD dwCtx,  
   BSTR * pbstrHelpString  
);  
```  
  
 `DLLGetDocumentation` Funkcja musi być Eksport zdefiniowany w pliku .def biblioteki dll.  
  
 Wewnętrznie pliku olb jest tworzony, który jest faktycznie biblioteki DLL. Ta biblioteka DLL zawiera jeden zasób, typu pliku biblioteki (.tlb) i jeden eksportowanych `DLLGetDocumentation`.  
  
 W przypadku plików .olb `helpstringdll` atrybut jest opcjonalny, ponieważ jest on tego samego pliku, który zawiera w samym pliku .tlb.  
  
 Można pobrać ciągów do wyświetlenia na **opisy** okienko, w związku z tym, co najmniej trzeba jest określić `helpstring` atrybutu w bibliotece typów. Jeśli chcesz, aby te ciągi, które mają zostać zlokalizowane, należy określić `helpstringdll` (opcjonalne) atrybutu i `helpstringcontext` atrybut (wymagane) i zaimplementuj `DLLGetDocumentation`.  
  
 Brak dodatkowych interfejsów, które muszą zostać zaimplementowane podczas pobierania informacji za pośrednictwem firmy idl `helpstringcontext` atrybutu i `DLLGetDocumentation`.  
  
 Innym sposobem uzyskania zlokalizowana nazwa i opis właściwości jest implementacja <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Aby uzyskać więcej informacji dotyczących implementacja tej metody, zobacz [właściwości pola i interfejsy okna](../extensibility/internals/properties-window-fields-and-interfaces.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Właściwości pola i interfejsy okna](../extensibility/internals/properties-window-fields-and-interfaces.md)   
 [Rozszerzanie właściwości](../extensibility/internals/extending-properties.md)   
 [helpstringdll —](http://msdn.microsoft.com/library/121271fa-f061-492b-b87f-bbfcf4b02e7b)   
 [HelpString —](http://msdn.microsoft.com/library/0401e905-a63e-4fad-98d0-d1efea111966)   
 [helpstringcontext —](http://msdn.microsoft.com/library/d4cd135e-d91c-4aa3-9353-8aeb096f52cf)   
 [helpcontext —](http://msdn.microsoft.com/library/6fbb022d-a4b7-4989-a02f-7f18a9b0ad96)   
 [helpfile](http://msdn.microsoft.com/library/d75161c1-1363-4019-ae09-e7e3b8a3971e)   
 [lcid](http://msdn.microsoft.com/library/7f248c69-ee1c-42c3-9411-39cf27c9f43d)