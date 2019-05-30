---
title: Zasoby w pakietach VSPackage | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 3abcfebb7bbcc0eaa6a05760de4531f020b41ddb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318728"
---
# <a name="resources-in-vspackages"></a>Zasoby w pakietach VSPackage
Zlokalizowane zasoby można osadzić w natywnych satelitarnej biblioteki DLL interfejsu użytkownika, zarządzanych satelickich bibliotek DLL, lub zarządzanych pakietu VSPackage, sam.

 Niektóre zasoby nie mogą być osadzone w pakietach VSPackage. Następujące typy zarządzane mogą być osadzone:

- Ciągi

- Klucze ładowania pakietów, (które są również ciągi)

- Narzędzie okna ikony

- Skompilowane pliki danych wyjściowych tabeli poleceń (stosunku)

- Mapy bitowe Dyrektor ds. technologii

- Pomoc wiersza polecenia

- Dane okna dialogowego — informacje

  Zasoby w pakiecie zarządzane są wybierane przez identyfikator zasobu. Wyjątek stanowi pliku Dyrektor ds. technologii, który musi mieć nazwę CTMENU. Plik Dyrektor ds. technologii musi znajdować się w tabeli zasobów jako `byte[]`. Wszystkie inne elementy zasobów są identyfikowane przez typ.

  Możesz użyć <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> atrybutu w celu wskazania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dostępnych zasobów zarządzanych.

  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]

  Ustawienie <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> w ten sposób oznacza, że [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] powinien ignorować niezarządzanych satelickich bibliotek DLL, podczas wyszukiwania zasobów, na przykład za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>. Jeśli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] napotka dwóch lub więcej zasobów, które mają ten sam identyfikator zasobu używa pierwszego zasobu, które znajdzie.

## <a name="example"></a>Przykład
 Poniższy przykład jest reprezentację zarządzanych ikonę okna narzędzia.

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

 Poniższy przykład pokazuje, jak osadzać tablicy bajtów Dyrektor ds. technologii, która musi mieć nazwę CTMENU.

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
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ładowanie pakietów VSPackage, jeśli to możliwe w opóźnienia. Osadzanie pliku Dyrektor ds. technologii w VSPackage konsekwencją jest fakt, że [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] należy załadować takich VSPackages w pamięci podczas instalacji, który jest podczas tworzenia tabeli scalonych polecenia. Zasoby można wyodrębnić z pakietu VSPackage, sprawdzając metadanych bez uruchamiania kodu w pakietu VSPackage. Nie zainicjowano pakietu VSPackage w tej chwili, więc jest minimalne utrata wydajności.

 Gdy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] żądań zasobów z pakietu VSPackage po zakończeniu instalacji, ten pakiet jest prawdopodobnie już załadowany i zainicjowany, więc jest minimalne utrata wydajności.

## <a name="see-also"></a>Zobacz też
- [Zarządzanie pakietami VSPackage](../../extensibility/managing-vspackages.md)
- [Zasoby zlokalizowane w aplikacjach MFC: biblioteki DLL Satellite](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
