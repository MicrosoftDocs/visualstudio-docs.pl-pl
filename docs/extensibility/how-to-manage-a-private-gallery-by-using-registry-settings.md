---
title: Zarządzanie galerią prywatną przy użyciu ustawień rejestru
description: Dowiedz się, jak kontrolować dostęp do kontrolek, szablonów i narzędzi w galerii Visual Studio, Galerii przykładów lub galerii prywatnych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9fef1e6447ac07e9c3d4ccfb76a9ee1e06f91e42
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898838"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Samodzielnie: zarządzanie galerią prywatną przy użyciu ustawień rejestru
Jeśli jesteś administratorem lub deweloperem rozszerzenia programu Isolated Shell, możesz kontrolować dostęp do kontrolek, szablonów i narzędzi w galerii Visual Studio, galerii przykładów lub galerii prywatnych. Aby udostępnić galerię lub jej niedostępność, utwórz plik *pkgdef* opisujący zmodyfikowane klucze rejestru i ich wartości.

## <a name="manage-private-galleries"></a>Zarządzanie galeriami prywatnymi
 Aby kontrolować dostęp do galerii na wielu komputerach, można utworzyć plik *pkgdef.* Ten plik musi mieć następujący format.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom Feed|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 Klucz `Repositories` odwołuje się do galerii, która ma być włączona lub wyłączona. Galeria Visual Studio i Galeria przykładów używają następujących identyfikatorów GUID repozytorium:

- Visual Studio Gallery : 0F45E408-7995-4375-9485-86B8DB553DC9

- Galeria przykładów: AEB9CB40-D8E6-4615-B52C-27E307F8506C

  Wartość `Disabled` jest opcjonalna. Galeria jest domyślnie włączona.

  Wartość `Priority` określa kolejność, w jakiej galerie są wyświetlane w **oknie dialogowym** Opcje. Visual Studio Ma priorytet 10, a galeria przykładów ma priorytet 20. Galerie prywatne zaczynają się od priorytetu 100. Jeśli kilka galerii ma taką samą wartość priorytetu, kolejność ich pojawiania się jest określana przez wartości ich `DisplayName` zlokalizowanych atrybutów.

  Ta `Protocol` wartość jest wymagana w przypadku galerii opartych na atomach lub w programie SharePoint.

  Należy `DisplayName` określić wartości , lub oba te wartości i `DisplayNameResourceID` `DisplayNamePackageGuid` . Jeśli wszystkie są określone, używana `DisplayNameResourceID` jest para i `DisplayNamePackageGuid` .

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>Wyłączanie galerii Visual Studio użyciu pliku pkgdef
 Galerię można wyłączyć w *pliku pkgdef.* Poniższy wpis wyłącza Visual Studio Galerii:

```
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]
"Disabled"=dword:00000001

```

 Poniższy wpis wyłącza galerię przykładów:

```
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]
"Disabled"=dword:00000001

```

## <a name="see-also"></a>Zobacz też
- [Galerie prywatne](../extensibility/private-galleries.md)
