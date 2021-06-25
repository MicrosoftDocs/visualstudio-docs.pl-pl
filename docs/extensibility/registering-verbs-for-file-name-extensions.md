---
title: Rejestrowanie zleceń dla rozszerzeń nazw plików | Microsoft Docs
description: Dowiedz się, jak zarejestrować zlecenie skojarzone z identyfikatorem programowym rozszerzenia nazwy pliku przy użyciu klucza powłoki.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c223dea7e265d8d040d502c99ded09380e89690f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901230"
---
# <a name="register-verbs-for-file-name-extensions"></a>Rejestrowanie zleceń dla rozszerzeń nazw plików
Skojarzenie rozszerzenia nazwy pliku z aplikacją zazwyczaj ma preferowaną akcję, która występuje, gdy użytkownik dwukrotnie kliknie plik. Ta preferowana akcja jest połączona z czasownikiem, na przykład otwartym, który odpowiada akcji.

 Czasowniki skojarzone z identyfikatorem programowym (ProgID) rozszerzenia można zarejestrować przy użyciu klucza powłoki znajdującego się HKEY_CLASSES_ROOT **\{ progid}\shell.** Aby uzyskać więcej informacji, zobacz [Typy plików](/windows/desktop/shell/fa-file-types).

## <a name="register-standard-verbs"></a>Rejestrowanie standardowych zleceń
 System operacyjny rozpoznaje następujące standardowe czasowniki:

- Otwórz

- Edytuj

- Graj.

- Drukuj

- Wersja zapoznawcza

  Jeśli to możliwe, zarejestruj standardowe zlecenie. Najpopularniejszym wyborem jest czasownik Otwórz. Zlecenia Edytuj należy używać tylko wtedy, gdy istnieje jasna różnica między otwieraniem pliku a edytowaniem pliku. Na przykład otwarcie pliku *.htm* wyświetla go w przeglądarce, podczas gdy edytowanie pliku *.htm* uruchamia edytor HTML. Standardowe czasowniki są zlokalizowane przy użyciu opcji regionalnych systemu operacyjnego.

> [!NOTE]
> Podczas rejestrowania standardowych zleceń nie należy ustawiać wartości domyślnej dla klucza Otwórz. Wartość domyślna zawiera ciąg wyświetlany w menu. System operacyjny dostarcza ten ciąg dla standardowych czasowników.

 Pliki projektu należy zarejestrować, aby uruchomić nowe wystąpienie klasy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , gdy użytkownik otworzy plik. Poniższy przykład ilustruje standardową rejestrację czasownika dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektu.

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

 Aby otworzyć plik w istniejącym wystąpieniu programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , zarejestruj klucz DDEEXEC. Poniższy przykład ilustruje standardową rejestrację czasownika dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] *pliku cs.*

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

## <a name="set-the-default-verb"></a>Ustawianie czasownika domyślnego
 Czasownik domyślny to akcja wykonywana, gdy użytkownik kliknie dwukrotnie plik w Eksplorator Windows. Czasownik domyślny to czasownik określony jako wartość domyślna dla HKEY_CLASSES_ROOT **\\ *progid*\Shell** key. Jeśli żadna wartość nie zostanie określona, czasownik domyślny jest pierwszym czasownikiem określonym w **HKEY_CLASSES_ROOT \\ *progid*\Shell** key list.

> [!NOTE]
> Jeśli planujesz zmienić domyślne zlecenie dla rozszerzenia we wdrożeniu side-by-side, należy wziąć pod uwagę wpływ na instalację i usuwanie. Podczas instalacji oryginalna wartość domyślna jest zastępowana.

## <a name="see-also"></a>Zobacz też
- [Zarządzanie skojarzeniami plików obok siebie](../extensibility/managing-side-by-side-file-associations.md)
