---
title: Extern, Element | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 17477b7eb60aa332f6910019e28f4c53aa31ebf1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204395"
---
# <a name="extern-element"></a>Extern, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Extern, element odwołuje się do żadnych plików zewnętrzne nagłówków (.h) do scalenia przy użyciu pliku vsct w czasie kompilacji. Pliki do scalenia muszą znajdować się w ścieżce Include podane do kompilatora VSCT lub jest przywoływany przez [obejmują Element](../extensibility/include-element.md). Pliki mogą być inne .vsct — pliki lub pliki nagłówkowe C++.  
  
 Definicje w plikach nagłówkowych musi mieć postać "#define [Symbol] [wartość]" wartość może być inny symbol, jeśli został wcześniej zdefiniowany. Definicje mogą być używane w instrukcjach warunkowych elementów polecenia. Dowolny symbol nie rzeczywistej zostaną odrzucone.  
  
 CommandTable, element  
Extern, element  
  
## <a name="syntax"></a>Składnia  
  
```  
<Extern href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|{1&gt;href&lt;1}|Wymagany. Ścieżka do pliku nagłówka:<br /><br /> href="stdidcmd.h"|  
|Warunek|Opcjonalna. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
|język|Opcjonalny. Domyślny język wszystkich [ \<ciągi >](../extensibility/strings-element.md) elementów w tabeli poleceń:<br /><br /> Language = "en-us"|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Brak.|Brak.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[CommandTable, element](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy, które reprezentują poleceń — czyli elementy menu, menu, paski narzędzi i pola kombi — zapewniającej pakietu VSPackage IDE.|  
  
## <a name="example"></a>Przykład  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-  
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>  
    …  
  <Commands package="guidMyPackage">  
</CommandTable>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tabeli poleceń programu Visual Studio (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Jak dodać elementy interfejsu użytkownika w pakietach VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
