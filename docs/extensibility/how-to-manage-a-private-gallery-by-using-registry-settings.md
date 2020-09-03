---
title: 'Instrukcje: Zarządzanie galerią prywatną za pomocą ustawień rejestru | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2630fc71bea40a4d05e616ae336759ba62431a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710931"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Instrukcje: Zarządzanie galerią prywatną przy użyciu ustawień rejestru
Jeśli jesteś administratorem lub deweloperem rozszerzenia izolowanej powłoki, możesz kontrolować dostęp do kontrolek, szablonów i narzędzi w galerii programu Visual Studio, galerii przykładów lub w galeriach prywatnych. Aby udostępnić galerię lub niedostępny, Utwórz plik *. pkgdef* , który opisuje zmodyfikowane klucze rejestru i ich wartości.

## <a name="manage-private-galleries"></a>Zarządzaj prywatnymi galeriami
 Można utworzyć plik *. pkgdef* , aby kontrolować dostęp do galerii na wielu komputerach. Ten plik musi mieć następujący format.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom Feed|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 `Repositories`Klucz odnosi się do galerii, która ma być włączona lub wyłączona. Galeria programu Visual Studio i Galeria przykładów używają następujących identyfikatorów GUID repozytorium:

- Galeria programu Visual Studio: 0F45E408-7995-4375-9485-86B8DB553DC9

- Galeria przykładów: AEB9CB40-D8E6-4615-B52C-27E307F8506C

  `Disabled`Wartość jest opcjonalna. Domyślnie Galeria jest włączona.

  `Priority`Wartość określa kolejność, w jakiej Galerie są wyświetlane w oknie dialogowym **Opcje** . Galeria programu Visual Studio ma priorytet 10, a Galeria przykładów ma priorytet 20. Galerie prywatne zaczynają się od priorytetu 100. Jeśli kilka galerii ma taką samą wartość priorytetu, kolejność, w jakiej są one wyświetlane, zależy od wartości zlokalizowanych `DisplayName` atrybutów.

  Ta `Protocol` wartość jest wymagana dla galerii opartych na protokole Atom lub programie SharePoint.

  `DisplayName`Należy określić albo oba, `DisplayNameResourceID` jak i `DisplayNamePackageGuid` . Jeśli wszystkie są określone, `DisplayNameResourceID` `DisplayNamePackageGuid` para i jest używana.

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>Wyłączenie galerii programu Visual Studio przy użyciu pliku. pkgdef
 Możesz wyłączyć galerię w pliku *. pkgdef* . Następujący wpis wyłącza galerię programu Visual Studio:

```
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]
"Disabled"=dword:00000001

```

 Następujący wpis wyłącza galerię przykładów:

```
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]
"Disabled"=dword:00000001

```

## <a name="see-also"></a>Zobacz też
- [Galerie prywatne](../extensibility/private-galleries.md)
