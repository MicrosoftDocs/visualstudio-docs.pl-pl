---
title: UsedCommand, Element | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ccc96d92e83ea42c6921abd2159499c1e9c42c4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54930358"
---
# <a name="usedcommand-element"></a>UsedCommand, element
Umożliwia pakietu VSPackage w celu dostępu do poleceń, która jest zdefiniowana w innym pliku vsct. Na przykład, jeśli Twoja pakietu VSPackage używa standardu **kopiowania** polecenia, która jest zdefiniowana przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] powłoki, możesz dodać polecenie menu lub pasek narzędzi bez jej ponownego wdrażania.  
  
## <a name="syntax"></a>Składnia  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Identyfikator GUID|Wymagana. Identyfikator GUID pary identyfikator GUID, który identyfikuje polecenie.|  
|identyfikator|Wymagana. Identyfikator pary identyfikator GUID, który identyfikuje polecenie.|  
|Warunek|Opcjonalna. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Brak||  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[UsedCommands, element](../extensibility/usedcommands-element.md)|Grupuje elementy UsedCommand i inne grupy UsedCommands.|  
  
## <a name="remarks"></a>Uwagi  
 Dodając polecenie do `<UsedCommands>` informuje pakietu VSPackage elementu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] środowiska, że pakietu VSPackage wymaga polecenia. Należy dodać `<UsedCommand>` elementu dla dowolnego polecenia wymaga pakietu nie została uwzględniona we wszystkich wersjach i konfiguracji programu Visual Studio. Na przykład, jeśli pakiet wywołuje polecenie, które są specyficzne dla języka Visual C++, polecenie nie będzie dostępne dla użytkowników programu Visual Web Developer, chyba że dodasz `<UsedCommand>` elementu dla polecenia.  
  
## <a name="example"></a>Przykład  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [UsedCommands, Element](../extensibility/usedcommands-element.md)   
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)