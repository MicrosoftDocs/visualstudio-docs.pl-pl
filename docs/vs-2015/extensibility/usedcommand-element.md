---
title: UsedCommand — element | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 91929038d77bcf14c6997f9b60551ed8c9c3b820
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186368"
---
# <a name="usedcommand-element"></a>UsedCommand, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Umożliwia pakietu VSPackage dostęp do polecenia, które jest zdefiniowane w innym pliku. vsct. Na przykład jeśli pakietu VSPackage używa polecenia **kopiowania** standardowego, które jest zdefiniowane przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] powłokę, można dodać polecenie do menu lub paska narzędzi bez jego ponownego wdrożenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|guid|Wymagany. Identyfikator GUID pary identyfikatora identyfikatora GUID, który identyfikuje polecenie.|  
|identyfikator|Wymagany. Identyfikator pary identyfikatorów identyfikatora GUID, który identyfikuje polecenie.|  
|Warunek|Opcjonalny. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Brak||  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[UsedCommands, element](../extensibility/usedcommands-element.md)|Grupuje elementy UsedCommand i inne grupy UsedCommands.|  
  
## <a name="remarks"></a>Uwagi  
 Dodając polecenie do `<UsedCommands>` elementu, pakietu VSPackage informuje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] środowisko, że pakietu VSPackage wymaga polecenia. Należy dodać `<UsedCommand>` element dla każdego polecenia wymaganego przez pakiet, które mogą nie być dołączone do wszystkich wersji i konfiguracji programu Visual Studio. Na przykład jeśli pakiet wywołuje polecenie, które jest specyficzne dla Visual C++, polecenie nie będzie dostępne dla użytkowników programu Visual Web Developer, chyba że zostanie dołączony `<UsedCommand>` element dla polecenia.  
  
## <a name="example"></a>Przykład  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [UsedCommands, element](../extensibility/usedcommands-element.md)   
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
