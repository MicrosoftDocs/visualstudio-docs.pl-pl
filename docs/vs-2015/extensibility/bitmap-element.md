---
title: Bitmap, Element | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cbeb175c8e4f9902fafbfdb8df4f5d83387980a4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789944"
---
# <a name="bitmap-element"></a>Bitmap, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definiuje mapę bitową. Mapa bitowa jest ładowany z zasobu lub z pliku.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Identyfikator GUID|Wymagana. Identyfikator GUID identyfikatora polecenia identyfikator GUID/ID.<br /><br /> Atrybut guid dla mapy bitowej nie jest skojarzony z dowolnego pakietu VSPackage lub inne grupy poleceń.  Powinna mieć unikatowe dla definicji mapy bitowej i nie powinna być używana do żadnych innych celów.|  
|Atrybut resID|Identyfikator GUID/ID identyfikator polecenia. Wymagany jest resID lub atrybut href.<br /><br /> Atrybut resID jest identyfikator zasobu liczba całkowita, określająca paska mapy bitowej, który ma być załadowane podczas tabeli poleceń scalania.  Podczas ładowania tabeli poleceń, mapy bitowe, określonego przez identyfikator zasobu zostaną załadowane z zasobu tego samego modułu.|  
|usedList|Wymagane, jeśli atrybut resID jest obecny. Wybiera dostępne obrazy paska mapy bitowej.|  
|href|Ścieżka do mapy bitowej. Wymagany jest resID lub atrybut href.<br /><br /> Ścieżka include jest wyszukiwana w plik wskazany obraz, który jest osadzony w wynikowego pliku binarnego.  Polecenie scalania tabeli obraz, który jest kopiowany, a nie wyszukiwanie dodatkowych zasobów obciążenia jest wymagana ani.  Jeśli nie ma atrybutu usedList, wszystkie obrazy w pasku są dostępne. **Uwaga:** obrazy mogą być dostarczane w jednym z kilku formatów, które zawierają bmp, PNG i .gif.  Wcześniejsze wersje kompilatora nie obsługiwał obrazy bitmapowe 32-bitowych, których dane alfa przezroczystości częściowe. Obejście problemu w przypadku tych wersji jest w formacie PNG.|  
|Warunek|Opcjonalna. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
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

