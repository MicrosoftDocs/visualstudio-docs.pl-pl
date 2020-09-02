---
title: Pobieranie opisów pól z okna właściwości | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Properties window, field descriptions
ms.assetid: 7d92bb6a-b9b9-4cd8-99e9-b5ee129b52a3
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 1d2b152fd7ed517a238f9893320bd0c36035627c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703982"
---
# <a name="getting-field-descriptions-from-the-properties-window"></a>Pobieranie opisów pól z okna właściwości
W dolnej części okna **Właściwości** obszar opisu zawiera informacje związane z wybranym polem właściwości. Ta funkcja jest domyślnie włączona. Jeśli chcesz ukryć pole Opis, kliknij prawym przyciskiem myszy okno **Właściwości** , a następnie kliknij pozycję **Opis**. Spowoduje to również usunięcie znacznika wyboru obok tytułu **opisu** w oknie menu. Możesz ponownie wyświetlić pole, wykonując te same kroki, aby ponownie włączyć **Opis** .  
  
 Informacje w polu Opis pochodzą z <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> . Każda metoda, interfejs, Klasa coclass i tak dalej może mieć atrybut nielokalny `helpstring` w bibliotece typów. Okno **Właściwości** Pobiera ciąg z <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A> .  
  
### <a name="to-specify-localized-help-strings"></a>Aby określić zlokalizowane ciągi pomocy  
  
1. Dodaj `helpstringdll` atrybut do instrukcji Library w bibliotece typów ( `typelib` ).  
  
   > [!NOTE]
   > Ten krok jest opcjonalny, jeśli biblioteka typów znajduje się w pliku biblioteki obiektów (. olb).  
  
2. Określ `helpstringcontext` atrybuty dla ciągów. Można również określić `helpstring` atrybuty.  
  
    Te atrybuty są różne od `helpfile` atrybutów i `helpcontext` , które są zawarte w pliku. chm.  
  
   Aby pobrać informacje o opisach, które mają być wyświetlane dla wyróżnionej nazwy właściwości, okno **Właściwości** wywołuje <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> dla wybranej właściwości, określając żądany `lcid` atrybut ciągu danych wyjściowych. Wewnętrznie program <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> znajduje plik. dll określony w `helpstringdll` atrybucie i wywołuje plik DLL `DLLGetDocumentation` z określonym kontekstem i `lcid` atrybutem.  
  
   Sygnatura i implementacja programu `DLLGetDocumentation` są:  
  
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
  
 `DLLGetDocumentation`Funkcja musi być eksportem zdefiniowanym w pliku. def dla biblioteki DLL.  
  
 Wewnętrznie tworzony jest plik. olb, który jest w rzeczywistości biblioteką DLL. Ta biblioteka DLL zawiera jeden zasób, plik biblioteki typów (. tlb) i jedną funkcję, która została wyeksportowana `DLLGetDocumentation` .  
  
 W przypadku plików. olb `helpstringdll` atrybut jest opcjonalny, ponieważ jest to ten sam plik, który zawiera sam plik. tlb.  
  
 Aby ciągi były wyświetlane w okienku **opisy** , w związku z tym minimalnym wymaganiem jest określenie `helpstring` atrybutu w bibliotece typów. Jeśli chcesz, aby te ciągi były zlokalizowane, musisz określić `helpstringdll` atrybut (opcjonalnie) i `helpstringcontext` atrybut (required) i zaimplementować `DLLGetDocumentation` .  
  
 Nie ma dodatkowych interfejsów, które należy zaimplementować podczas uzyskiwania zlokalizowanych informacji przy użyciu atrybutu IDL `helpstringcontext` i `DLLGetDocumentation` .  
  
 Innym sposobem uzyskania zlokalizowanej nazwy i opisu właściwości jest implementacja <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A> . Aby uzyskać więcej informacji dotyczących implementacji tej metody, zobacz [okno właściwości pola i interfejsy](../extensibility/internals/properties-window-fields-and-interfaces.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Pola i interfejsy okna właściwości](../extensibility/internals/properties-window-fields-and-interfaces.md)   
 [Rozszerzanie właściwości](../extensibility/internals/extending-properties.md)   
 [helpstringdll](https://msdn.microsoft.com/library/121271fa-f061-492b-b87f-bbfcf4b02e7b)   
 [helpstring](https://msdn.microsoft.com/library/0401e905-a63e-4fad-98d0-d1efea111966)   
 [helpstringcontext](https://msdn.microsoft.com/library/d4cd135e-d91c-4aa3-9353-8aeb096f52cf)   
 [atrybut HelpContext](https://msdn.microsoft.com/library/6fbb022d-a4b7-4989-a02f-7f18a9b0ad96)   
 [HelpFile](https://msdn.microsoft.com/library/d75161c1-1363-4019-ae09-e7e3b8a3971e)   
 [lcid](https://msdn.microsoft.com/library/7f248c69-ee1c-42c3-9411-39cf27c9f43d)