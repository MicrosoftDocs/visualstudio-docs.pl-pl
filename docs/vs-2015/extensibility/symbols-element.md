---
title: Symbols — element | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c8d28d225bd3a8d5c105bf54b9c63574002aed15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160457"
---
# <a name="symbols-element"></a>Symbols, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definiuje identyfikatory GUID i identyfikatorów, które są używane przez inne elementy VSCT. W przypadku kodu niezarządzanego te informacje zazwyczaj pochodzą z plików nagłówkowych, które są określone przez [element extern](../extensibility/extern-element.md). Kod zarządzany używa elementów podrzędnych elementu Symbols do definiowania tych informacji.  
  
 Jeśli utworzysz plik. vsct z istniejącego pliku. Dyrektor ds, symbole zostaną wygenerowane jako elementy podrzędne elementu symboli. Aby uzyskać więcej informacji, zobacz [How to: Create a. Plik vsct z istniejącego. Plik dyrektor ds](../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
 Elementu Symbols nie należy mylić z [elementem define](../extensibility/define-element.md), który definiuje pary nazwa-wartość do użycia przez preprocesor.  
  
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
|GuidSymbol|Definiuje symbol GUID. GuidSymbol ma dwa wymagane atrybuty: Name i value. Nazwa jest nazwą symbolu, a wartość jest wartością identyfikatora GUID w postaci ciągu.<br /><br /> Na przykład:\<GuidSymbol name="guidVsPackage1Pkg"   value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />|  
|IDSymbol|Definiuje symbol. IDSymbol ma dwa wymagane atrybuty: Name i value. Nazwa jest nazwą symbolu, a wartość jest wartością symbolu jako ciąg.<br /><br /> Na przykład:\<IDSymbol name="MyMenuGroup" value="0x1020" />|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[CommandTable, element](../extensibility/commandtable-element.md)|Element główny pliku. vsct.|  
  
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
