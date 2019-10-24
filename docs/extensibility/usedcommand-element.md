---
title: UsedCommand — element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44ea8f27cafb166968f66c53dc68398526e0aa5d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718770"
---
# <a name="usedcommand-element"></a>UsedCommand, element
Umożliwia pakietu VSPackage dostęp do polecenia, które jest zdefiniowane w innym pliku. vsct. Na przykład jeśli pakietu VSPackage używa polecenia **kopiowania** standardowego, które jest zdefiniowane przez powłokę [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], można dodać polecenie do menu lub paska narzędzi bez jego ponownego wdrożenia.

## <a name="syntax"></a>Składnia

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|Ident|Wymagany. Identyfikator GUID pary identyfikatora identyfikatora GUID, który identyfikuje polecenie.|
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
 Dodając polecenie do elementu `<UsedCommands>`, pakietu VSPackage informuje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] środowiska, że pakietu VSPackage wymaga polecenia. Należy dodać element `<UsedCommand>` dla każdego polecenia wymaganego przez pakiet, które mogą nie być dołączone do wszystkich wersji i konfiguracji programu Visual Studio. Na przykład jeśli pakiet wywołuje polecenie, które jest specyficzne dla wizualizacji C++, polecenie nie będzie dostępne dla użytkowników programu Visual Web Developer, chyba że zostanie uwzględniony `<UsedCommand>` element dla polecenia.

## <a name="example"></a>Przykład

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>Zobacz także
- [UsedCommands, element](../extensibility/usedcommands-element.md)
- [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)