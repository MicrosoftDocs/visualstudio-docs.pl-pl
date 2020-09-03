---
title: Element bitmapy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc1fb57c7ec43421b211b29cfd6ab97b24a1864c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184744"
---
# <a name="bitmap-element"></a>Bitmap, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definiuje mapę bitową. Mapa bitowa jest ładowana z zasobu lub z pliku.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|guid|Wymagany. Identyfikator GUID identyfikatora polecenia GUID/ID.<br /><br /> Atrybut GUID dla mapy bitowej nie jest skojarzony z żadną pakietu VSPackage lub inną grupą poleceń.  Powinna być unikatowa dla definicji mapy bitowej i nie powinna być używana w żadnym innym celu.|  
|resID|Identyfikator identyfikatora polecenia GUID/ID. Wymagany jest atrybut resID lub href.<br /><br /> Atrybut resID jest IDENTYFIKATORem zasobu liczb całkowitych, który określa pasek mapy bitowej, który ma zostać załadowany podczas scalania tabeli poleceń.  Po załadowaniu tabeli poleceń mapy bitowe określone przez identyfikator zasobu zostaną załadowane z zasobu tego samego modułu.|  
|usedList|Wymagany, jeśli jest obecny atrybut resID. Wybiera dostępne obrazy na pasku mapy bitowej.|  
|Tag|Ścieżka do mapy bitowej. Wymagany jest atrybut resID lub href.<br /><br /> Ścieżka include szuka wskazanego pliku obrazu, który jest osadzony w danych binarnych.  Podczas scalania tabeli poleceń obraz jest kopiowany i nie są wymagane żadne dodatkowe Wyszukiwanie zasobów ani obciążenie.  Jeśli atrybut usedList nie istnieje, wszystkie obrazy na pasku są dostępne. **Uwaga:**  Obrazy mogą być dostarczane w jednym z kilku formatów, które zawierają pliki BMP, PNG i. gif.  Wcześniejsze wersje kompilatora nie obsługują obrazów mapy bitowej 32-bitowych, które mają informacje alfa dla częściowej przejrzystości. Obejście tych wersji ma zastosowanie w formacie PNG.|  
|Warunek|Opcjonalny. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Bitmaps, element](../extensibility/bitmaps-element.md)|Grupuje elementy mapy bitowej.|  
  
## <a name="example"></a>Przykład  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
