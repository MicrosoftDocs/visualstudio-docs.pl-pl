---
title: Zasoby w pakietów VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07e1e19f802203b9770764330ea894b7d0eb98b8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724154"
---
# <a name="resources-in-vspackages"></a>Zasoby w pakietach VSPackage
Zlokalizowane zasoby można osadzać w natywnych bibliotekach DLL interfejsu użytkownika, zarządzanej satelitarnej biblioteki DLL lub w zarządzanym pakietu VSPackage.

 Niektórych zasobów nie można osadzić w pakietów VSPackage. Można osadzić następujące typy zarządzane:

- Ciągi

- Klucze ładowania pakietu (które są również ciągami)

- Ikony okna narzędzi

- Skompilowane pliki wyjściowe tabeli poleceń (Dyrektor ds)

- Mapy bitowe dyrektor ds

- Pomoc wiersza polecenia

- Dane okna dialogowego — Informacje

  Zasoby w pakiecie zarządzanym są wybierane według identyfikatora zasobu. Wyjątkiem jest plik dyrektor ds, który musi mieć nazwę CTMENU. Plik dyrektor ds musi znajdować się w tabeli zasobów jako `byte[]`. Wszystkie inne elementy zasobów są identyfikowane według typu.

  Można użyć atrybutu <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, aby wskazać, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] są dostępne zarządzane zasoby.

  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]

  Ustawienie <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> w ten sposób oznacza, że [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] powinny ignorować niezarządzane, satelitarne biblioteki dll podczas wyszukiwania zasobów, na przykład przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>. Jeśli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] napotka dwa lub więcej zasobów, które mają ten sam identyfikator zasobu, używa pierwszego znalezionego zasobu.

## <a name="example"></a>Przykład
 Poniższy przykład jest zarządzaną reprezentacją ikony okna narzędzi.

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

 W poniższym przykładzie pokazano, jak osadzić tablicę bajtów dyrektor ds, która musi mieć nazwę CTMENU.

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
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] opóźnia ładowanie pakietów VSPackage, gdy jest to możliwe. Wynikiem osadzenia pliku dyrektor ds w pakietu VSPackage jest to, że [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] musi załadować wszystkie takie pakietów VSPackage w pamięci podczas instalacji, co jest wynikiem kompilacji Scalonej tabeli poleceń. Zasoby można wyodrębnić z pakietu VSPackage, sprawdzając metadane bez uruchamiania kodu w pakietu VSPackage. W tej chwili nie zainicjowano pakietu VSPackage, więc utrata wydajności jest minimalna.

 Gdy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] żąda zasobu z pakietu VSPackage po zakończeniu instalacji, ten pakiet prawdopodobnie jest już załadowany i zainicjowany, więc utrata wydajności jest minimalna.

## <a name="see-also"></a>Zobacz także
- [Zarządzanie pakietami VSPackage](../../extensibility/managing-vspackages.md)
- [Zasoby zlokalizowane w aplikacjach MFC: biblioteki DLL Satellite](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
