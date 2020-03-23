---
title: -Edit (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Edit Devenv switch
- Devenv, /Edit switch
- /Edit Devenv switch
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d180d5a5d723d8085537f2993aac022d74df2c08
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595699"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)

Otwiera określony plik w istniejącym wystąpieniu programu Visual Studio.

## <a name="syntax"></a>Składnia

```shell
devenv /Edit [File1[ FileN]...]
```

## <a name="arguments"></a>Argumenty

- *Plik1*

  Element opcjonalny. Plik do otwarcia w istniejącym wystąpieniu programu Visual Studio. Jeśli nie istnieje żadne wystąpienie programu Visual Studio, zostanie utworzone nowe wystąpienie z uproszczonym układem okna, a narzędzie otworzy *plik1* w nowym wystąpieniu.

- *Plik*

  Element opcjonalny. Jeden lub więcej dodatkowych plików do otwarcia w istniejącym wystąpieniu programu Visual Studio.

## <a name="remarks"></a>Uwagi

Gdy plik nie jest określony, istniejące wystąpienie programu Visual Studio odbiera fokus. Jeśli nie określono pliku i nie istnieje wystąpienie programu Visual Studio, narzędzie tworzy wystąpienie z uproszczonym układem okna.

Jeśli istniejące wystąpienie programu Visual Studio jest w stanie modalnym, plik zostanie otwarty w istniejącym wystąpieniu, gdy program Visual Studio zakończy działanie stanu modalnego. Na przykład taka sytuacja może wystąpić, gdy [okno dialogowe Opcje](../../ide/reference/options-dialog-box-visual-studio.md) jest otwarte.

Jeśli więcej niż jedno wystąpienie programu Visual Studio jest otwarte, plik jest otwierany w ostatnio otwartym wystąpieniu.

## <a name="example"></a>Przykład

Pierwszy przykład otwiera `MyFile.cs` plik w istniejącym wystąpieniu programu Visual Studio. Jeśli wystąpienie programu Visual Studio nie istnieje, narzędzie otwiera plik w nowym wystąpieniu. Drugi przykład jest podobny, z tą różnicą, że otwiera trzy pliki zamiast tylko jednego pliku.

```shell
devenv /edit MyFile.cs

devenv /edit MyFile1.cs MyFile2.cs MyFile3.cs
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
