---
title: 'Porady: Zarządzanie galerią prywatną za pomocą ustawień rejestru | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 371fea42e1e59907c08d0a7e51a56875c1b73537
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51744456"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Porady: Zarządzanie galerią prywatną za pomocą ustawień rejestru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli jesteś administratorem lub deweloperem rozszerzenia Isolated Shell można kontrolować dostęp do formantów, szablonów i narzędzi dostępnych w galerii Visual Studio, galerii przykładów lub galerie prywatne. Aby galerii dostępne lub niedostępne, należy utworzyć plik .pkgdef, który opisuje zmodyfikowanych kluczy i ich wartości.  
  
## <a name="managing-private-galleries"></a>Zarządzanie galerie prywatne  
 Można utworzyć plik .pkgdef, aby kontrolować dostęp do galerii na wielu komputerach. Ten plik musi mieć następujący format.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 `Repositories` Klucz odnosi się do galerii, aby włączyć lub wyłączyć. W galerii Visual Studio i galerii przykładów należy użyć następujących repozytorium identyfikatorów GUID:  
  
- Galeria Visual Studio: 0F45E408-7995-4375-9485-86B8DB553DC9  
  
- Galeria przykładów: AEB9CB40-D8E6-4615-B52C-27E307F8506C  
  
  `Disabled` Wartość jest opcjonalna. Domyślnie galerii jest włączona.  
  
  `Priority` Wartość określa kolejność, w którym Galerie są wyświetlane w oknie dialogowym Opcje. Galeria Visual Studio ma priorytet 10 i galerii przykładów ma priorytet 20. Galerie prywatne start priorytetem 100. Jeśli kilka Galerie mają taką samą wartość priorytetu, kolejność, w jakiej są wyświetlane jest określana przez wartości ich zlokalizowane `DisplayName` atrybutów.  
  
  `Protocol` Wartość jest wymagana do galerii Atom lub programu SharePoint.  
  
  Albo `DisplayName`, i / lub `DisplayNameResourceID` i `DisplayNamePackageGuid`, musi być określona. Jeśli wszystkie są określone, a następnie `DisplayNameResourceID` i `DisplayNamePackageGuid` pary jest używany.  
  
## <a name="disabling-the-visual-studio-gallery-using-a-pkgdef-file"></a>Wyłączanie w galerii Visual Studio przy użyciu pliku pkgdef  
 Można wyłączyć galerii w pliku .pkgdef. Następujący wpis wyłącza galerii Visual Studio:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 Następujący wpis wyłącza galerii przykładów:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Galerie prywatne](../extensibility/private-galleries.md)

