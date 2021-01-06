---
title: Zasoby w pakietów VSPackage | Microsoft Docs
description: Dowiedz się, które typy zlokalizowanych zasobów można osadzić w pakietów VSPackage. Możesz również osadzić zasoby w natywnych bibliotekach DLL interfejsu użytkownika lub zarządzanych satelitarnych bibliotek DLL.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 2693d25e0b175a075bcc644077895076b75b7578
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875729"
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

  Zasoby w pakiecie zarządzanym są wybierane według identyfikatora zasobu. Wyjątkiem jest plik dyrektor ds, który musi mieć nazwę CTMENU. Plik dyrektor ds musi znajdować się w tabeli zasobów jako `byte[]` . Wszystkie inne elementy zasobów są identyfikowane według typu.

  Możesz użyć atrybutu, <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> Aby wskazać [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , że zarządzane zasoby są dostępne.

  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]

  Ustawienie <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> w ten sposób wskazuje, że [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] powinny być ignorowane niezarządzane satelity dll, gdy wyszukiwanie zasobów, na przykład przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A> . Jeśli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] napotka dwa lub więcej zasobów, które mają ten sam identyfikator zasobu, używa pierwszego znalezionego zasobu.

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
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] opóźnia ładowanie pakietów VSPackage, gdy jest to możliwe. Wynikiem osadzenia pliku dyrektor ds w pakietu VSPackage jest to, że [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] należy załadować wszystkie takie pakietów VSPackage w pamięci podczas instalacji, co jest możliwe podczas kompilacji Scalonej tabeli poleceń. Zasoby można wyodrębnić z pakietu VSPackage, sprawdzając metadane bez uruchamiania kodu w pakietu VSPackage. W tej chwili nie zainicjowano pakietu VSPackage, więc utrata wydajności jest minimalna.

 Gdy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] żąda zasobu z pakietu VSPackage po zakończeniu instalacji, ten pakiet prawdopodobnie jest już załadowany i zainicjowany, więc utrata wydajności jest minimalna.

## <a name="see-also"></a>Zobacz też
- [Zarządzanie pakietami VSPackage](../../extensibility/managing-vspackages.md)
- [Zlokalizowane zasoby w aplikacjach MFC: satelitarne biblioteki DLL](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
