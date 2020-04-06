---
title: 'Jak: Zarządzanie galerią prywatną przy użyciu ustawień rejestru | Dokumenty firmy Microsoft'
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710931"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Jak: Zarządzanie galerią prywatną przy użyciu ustawień rejestru
Jeśli jesteś administratorem lub twórcą rozszerzenia powłoki izolowanej, możesz kontrolować dostęp do formantów, szablonów i narzędzi w Galerii programu Visual Studio, Galerii próbek lub prywatnych galeriach. Aby udostępnić lub udostępnić galerię, utwórz plik *pkgdef* opisujący zmodyfikowane klucze rejestru i ich wartości.

## <a name="manage-private-galleries"></a>Zarządzanie prywatnymi galeriami
 Można utworzyć plik *pkgdef,* aby kontrolować dostęp do galerii na wielu komputerach. Ten plik musi mieć następujący format.

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

 Klucz `Repositories` odnosi się do galerii, która ma być włączona lub wyłączona. Galeria programu Visual Studio i Galeria przykładów używają następujących identyfikatorów GUID repozytorium:

- Galeria visual studio : 0F45E408-7995-4375-9485-86B8DB553DC9

- Galeria próbek : AEB9CB40-D8E6-4615-B52C-27E307F8506C

  Wartość `Disabled` jest opcjonalna. Domyślnie galeria jest włączona.

  Wartość `Priority` określa kolejność, w jakiej galerie są wymienione w oknie dialogowym **Opcje.** Galeria programu Visual Studio ma priorytet 10, a Galeria próbek ma priorytet 20. Prywatne galerie zaczynają się od priorytetu 100. Jeśli kilka galerii ma taką samą wartość priorytetu, kolejność, w `DisplayName` jakiej się pojawiają, zależy od wartości ich zlokalizowanych atrybutów.

  Wartość `Protocol` jest wymagana dla galerii opartych na atomach lub programie SharePoint.

  Należy `DisplayName`określić `DisplayNameResourceID` albo `DisplayNamePackageGuid`, albo oba i , należy określić. Jeśli wszystkie są określone, a następnie `DisplayNameResourceID` i `DisplayNamePackageGuid` pary jest używany.

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>Wyłączanie galerii programu Visual Studio przy użyciu pliku pkgdef
 Galerię można wyłączyć w pliku *pkgdef.* Poniższy wpis wyłącza Galerię programu Visual Studio:

```
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]
"Disabled"=dword:00000001

```

 Poniższy wpis wyłącza Galerię próbek:

```
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]
"Disabled"=dword:00000001

```

## <a name="see-also"></a>Zobacz też
- [Prywatne galerie](../extensibility/private-galleries.md)
