---
title: UsedCommand — element | Microsoft Docs
description: Element UsedCommand umożliwia pakietu VSPackage dostęp do polecenia, które jest zdefiniowane w innym pliku. vsct.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d1dcef25413bddbb1eb5c35a47a9dc0d30f4a8f
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715967"
---
# <a name="usedcommand-element"></a>UsedCommand, element
Umożliwia pakietu VSPackage dostęp do polecenia, które jest zdefiniowane w innym pliku. vsct. Na przykład jeśli pakietu VSPackage używa polecenia **kopiowania** standardowego, które jest zdefiniowane przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] powłokę, można dodać polecenie do menu lub paska narzędzi bez jego ponownego wdrożenia.

## <a name="syntax"></a>Składnia

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|guid|Wymagane. Identyfikator GUID pary identyfikatora identyfikatora GUID, który identyfikuje polecenie.|
|identyfikator|Wymagane. Identyfikator pary identyfikatorów identyfikatora GUID, który identyfikuje polecenie.|
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
 Dodając polecenie do `<UsedCommands>` elementu, pakietu VSPackage informuje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] środowisko, że pakietu VSPackage wymaga polecenia. Należy dodać `<UsedCommand>` element dla każdego polecenia wymaganego przez pakiet, które mogą nie być dołączone do wszystkich wersji i konfiguracji programu Visual Studio. Na przykład jeśli pakiet wywołuje polecenie, które jest specyficzne dla Visual C++, polecenie nie będzie dostępne dla użytkowników programu Visual Web Developer, chyba że zostanie dołączony `<UsedCommand>` element dla polecenia.

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
