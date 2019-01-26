---
title: 'Instrukcje: Zarządzanie galerią prywatną za pomocą ustawień rejestru | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5d75976ba9c677bb9b8f6c32623f81834471e10a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021523"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Instrukcje: Zarządzanie galerią prywatnej za pomocą ustawień rejestru
Jeśli jesteś administratorem lub deweloperem rozszerzenia Isolated Shell można kontrolować dostęp do formantów, szablonów i narzędzi dostępnych w galerii Visual Studio, galerii przykładów lub galerie prywatne. Aby galerii dostępne lub niedostępne, należy utworzyć *.pkgdef* pliku, który opisuje zmodyfikowanych kluczy i ich wartości.  
  
## <a name="manage-private-galleries"></a>Zarządzanie galerie prywatne  
 Możesz utworzyć *.pkgdef* plik, aby kontrolować dostęp do galerii na wielu komputerach. Ten plik musi mieć następujący format.  
  
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
  
 `Repositories` Klucz odnosi się do galerii, aby włączyć lub wyłączyć. W galerii Visual Studio i galerii przykładów należy użyć następujących repozytorium identyfikatorów GUID:  
  
- Visual Studio Gallery : 0F45E408-7995-4375-9485-86B8DB553DC9  
  
- Galeria przykładów: AEB9CB40-D8E6-4615-B52C-27E307F8506C  
  
  `Disabled` Wartość jest opcjonalna. Domyślnie galerii jest włączona.  
  
  `Priority` Wartość określa kolejność, w którym Galerie są wymienione w **opcje** okno dialogowe. Galeria Visual Studio ma priorytet 10 i galerii przykładów ma priorytet 20. Galerie prywatne start priorytetem 100. Jeśli kilka Galerie mają taką samą wartość priorytetu, kolejność, w jakiej są wyświetlane jest określana przez wartości ich zlokalizowane `DisplayName` atrybutów.  
  
  `Protocol` Wartość jest wymagana do galerii Atom lub programu SharePoint.  
  
  Albo `DisplayName`, i / lub `DisplayNameResourceID` i `DisplayNamePackageGuid`, musi być określona. Jeśli wszystkie są określone, a następnie `DisplayNameResourceID` i `DisplayNamePackageGuid` pary jest używany.  
  
## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>Wyłącz galerii Visual Studio przy użyciu pliku pkgdef  
 Można wyłączyć galerii w *.pkgdef* pliku. Następujący wpis wyłącza galerii Visual Studio:  
  
```  
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 Następujący wpis wyłącza galerii przykładów:  
  
```  
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Galerie prywatne](../extensibility/private-galleries.md)