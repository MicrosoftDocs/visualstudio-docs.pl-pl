---
title: Symbole Element | Dokumentacja firmy Microsoft
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
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6b9bccb3874d5b85a8a69288e2bf44adb14b5b3f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783249"
---
# <a name="symbols-element"></a>Symbols, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa identyfikatory GUID i identyfikatory, które są używane przez inne elementy VSCT. Dla niezarządzanego kodu, te informacje zazwyczaj pochodzą z pliki nagłówkowe, które są określone przez [Extern, Element](../extensibility/extern-element.md). Zarządzany kod używa elementów podrzędnych elementu symbole, aby zdefiniować te informacje.  
  
 Jeśli tworzysz pliku vsct z istniejącego pliku .cto symbole zostanie wygenerowany jako elementy podrzędne elementu symboli. Aby uzyskać więcej informacji, zobacz [porady: tworzenie. Plik Vsct z istniejącej. Dyrektor ds. technologii pliku](../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
 Symbols, element nie należy mylić z [zdefiniować Element](../extensibility/define-element.md), która definiuje pary nazwa wartość do użytku przez preprocesor.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Symbols>  
  <GuidSymbol>... </GuidSymbol>  
  <GuidSymbol>... </GuidSymbol>  
</Symbols>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Brak||  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|GuidSymbol|Definiuje symbol identyfikatora GUID. GuidSymbol ma dwa wymagane atrybuty: nazwę i wartość. Nazwa jest nazwą symbolu, a wartość jest wartością identyfikatora GUID jako ciąg.<br /><br /> Na przykład:\<GuidSymbol name = "guidVsPackage1Pkg" value = "{c5f54698-101a-4846-84d3-dc748f9cd848}" / >|  
|IDSymbol|Definiuje symbol. IDSymbol ma dwa wymagane atrybuty: nazwę i wartość. Nazwa jest nazwą symbolu, a wartość jest wartością symbolu jako ciąg.<br /><br /> Na przykład:\<IDSymbol name = "MyMenuGroup" value = "0x1020" / >|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[CommandTable, element](../extensibility/commandtable-element.md)|Element główny pliku vsct.|  
  
## <a name="example"></a>Przykład  
  
```  
<Symbols>  
  <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />  
  <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}">  
    <IDSymbol name="MyMenuGroup" value="0x1020" />  
    <IDSymbol name="cmdidMyCommand" value="0x0100" />  
    <IDSymbol name="cmdidMyTool" value="0x0101" />  
  </GuidSymbol>  
</Symbols>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

