---
title: Rejestrowanie czasowników dla rozszerzeń nazw plików | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac2854f1799075cc14d9beb557335be5228be21d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701531"
---
# <a name="register-verbs-for-file-name-extensions"></a>Rejestrowanie czasowników dla rozszerzeń nazw plików
Skojarzenie rozszerzenia nazwy pliku z aplikacją zwykle ma preferowaną akcję, która występuje, gdy użytkownik kliknie dwukrotnie plik. Ta preferowana akcja jest połączona z czasownikiem, na przykład Otwórz, który odpowiada akcji.

 Można zarejestrować zlecenia, które są skojarzone z identyfikatorem programowym (ProgID) dla rozszerzenia przy użyciu klucza powłoki znajdującego się w **HKEY_CLASSES_ROOT \{ ProgID} \shell**. Aby uzyskać więcej informacji, zobacz [typy plików](/windows/desktop/shell/fa-file-types).

## <a name="register-standard-verbs"></a>Zarejestruj czasowniki standardowe
 System operacyjny rozpoznaje następujące czasowniki standardowe:

- Otwarte

- Edytuj

- Graj.

- Drukowanie

- Wersja zapoznawcza

  Jeśli to możliwe, zarejestruj czasownik standardowy. Najbardziej typowym wyborem jest otwarty czasownik. Użyj zlecenia edycji tylko wtedy, gdy istnieje wyraźna różnica między otwieraniem pliku i edytowaniem pliku. Na przykład otwarcie pliku *. htm* powoduje wyświetlenie go w przeglądarce, podczas gdy Edycja pliku *. htm* powoduje uruchomienie edytora HTML. Czasowniki standardowe są zlokalizowane przy użyciu ustawień regionalnych systemu operacyjnego.

> [!NOTE]
> Podczas rejestrowania czasowników standardowych nie należy ustawiać wartości domyślnej dla otwartego klucza. Wartość domyślna zawiera ciąg wyświetlania w menu. System operacyjny dostarcza ten ciąg dla czasowników standardowych.

 Pliki projektu należy zarejestrować, aby uruchomić nowe wystąpienie, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gdy użytkownik otworzy plik. Poniższy przykład ilustruje standardowe rejestrację czasowników dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektu.

```
[HKEY_CLASSES_ROOT\.csproj]
@="VisualStudio.csproj.8.0"

[HKEY_CLASSES_ROOT\.csproj\OpenWithList]
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]
@=""

[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]
"VisualStudio.csproj.8.0"=""

[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]
@="C# Project file"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""
```

 Aby otworzyć plik w istniejącym wystąpieniu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , zarejestruj klucz ddeexec. Poniższy przykład ilustruje standardową rejestrację czasownikową dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] pliku *. cs* .

```
[HKEY_CLASSES_ROOT\.cs]
@="VisualStudio.cs.8.0"

[HKEY_CLASSES_ROOT\.cs\OpenWithList]
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]
@=""

[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]
"VisualStudio.cs.8.0"=""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]
@="C# Source file"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]
@="Open(\"%1\")"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]
@="VisualStudio.8.0"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]
@="system"
```

## <a name="set-the-default-verb"></a>Ustawianie domyślnego zlecenia
 Domyślne zlecenie jest akcją wykonywaną, gdy użytkownik kliknie dwukrotnie plik w Eksploratorze Windows. Domyślne zlecenie to zlecenie określone jako wartość domyślna HKEY_CLASSES_ROOT dla klucza ** \\ \Shell*ProgID*** . Jeśli żadna wartość nie zostanie określona, zlecenie domyślne to pierwsze zlecenie określone HKEY_CLASSES_ROOT na liście **kluczy \\ \Shell*ProgID*** .

> [!NOTE]
> Jeśli planujesz zmienić domyślne zlecenie rozszerzenia w ramach wdrożenia równoległego, weź pod uwagę wpływ instalacji i usuwania. Podczas instalacji oryginalna wartość domyślna jest zastępowana.

## <a name="see-also"></a>Zobacz też
- [Zarządzaj skojarzeniami plików obok siebie](../extensibility/managing-side-by-side-file-associations.md)
