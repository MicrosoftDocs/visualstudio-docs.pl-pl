---
title: Zasoby w pakietach VSPackage | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 493e9834e3d7cf6d82cebb8dd93d5369678c7be0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705600"
---
# <a name="resources-in-vspackages"></a>Zasoby w pakietach VSPackage
Zlokalizowane zasoby można osadzać w natywnych bibliotekach DLL interfejsu użytkownika, zarządzanych bibliotekach DLL satelitarnych lub w zarządzanym programie VSPackage.

 Niektóre zasoby nie mogą być osadzone w vspackages. Można osadzać następujące typy zarządzane:

- Ciągi

- Klucze ładowania pakietu (które są również ciągami)

- Ikony okien narzędzi

- Pliki Skompilowanych plików CTO (Compiled Command Table Output)

- Mapy bitowe CTO

- Pomoc wiersza polecenia

- Informacje o danych okna dialogowego

  Zasoby w pakiecie zarządzanym są wybierane według identyfikatora zasobu. Wyjątkiem jest plik CTO, który musi mieć nazwę CTMENU. Plik CTO musi być wyświetlany w `byte[]`tabeli zasobów jako plik . Wszystkie inne elementy zasobów są identyfikowane według typu.

  Można użyć <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> atrybutu, aby [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wskazać, że zasoby zarządzane są dostępne.

  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]

  Ustawienie <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> w ten sposób [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wskazuje, że należy ignorować niezarządzane biblioteki DLL satelity podczas wyszukiwania zasobów, na przykład za pomocą programu <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>. Jeśli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] napotka dwa lub więcej zasobów, które mają ten sam identyfikator zasobu, używa pierwszego zasobu, który znajdzie.

## <a name="example"></a>Przykład
 Poniższy przykład jest zarządzaną reprezentacją ikony okna narzędzia.

```
<data name="1001"
type="System.Resources.ResXFileRef,System.Windows.Forms">
     <value>
     MyToolWinIcon.bmp;
     System.Drawing.Bitmap,
     System.Drawing,
     Version=1.0.0.0,
     Culture=neutral,
     PublicKeyToken=b03f5f7f11d50a3a
     </value>
</data>
```

 W poniższym przykładzie pokazano, jak osadzić tablicę bajtów CTO, która musi mieć nazwę CTMENU.

```
<data name="CTMENU"
type="System.Resources.ResXFileRef,System.Windows.Forms">
     <value>
     MyPackage.cto;
     System.Byte[],
     mscorlib,
     Version=1.0.0.0,
     Culture=neutral,
     PublicKeyToken=b03f5f7f11d50a3a
     </value>
</data>
```

## <a name="implementation-notes"></a>Uwagi dotyczące implementacji
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]opóźnia ładowanie pakietów VSPackages, gdy tylko jest to możliwe. Konsekwencją osadzania pliku CTO w vsPackage jest to, że [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] musi załadować wszystkie takie VSPackages w pamięci podczas instalacji, czyli podczas tworzenia scalonej tabeli poleceń. Zasoby można wyodrębnić z vspackage przez badanie metadanych bez uruchamiania kodu w VSPackage. VSPackage nie jest inicjowany w tej chwili, więc utrata wydajności jest minimalna.

 Gdy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] żąda zasobu z VSPackage po instalacji, ten pakiet może być już załadowany i zainicjowany, więc utrata wydajności jest minimalna.

## <a name="see-also"></a>Zobacz też
- [Zarządzanie pakietami VSPackage](../../extensibility/managing-vspackages.md)
- [Zasoby zlokalizowane w aplikacjach MFC: biblioteki DLL Satellite](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
