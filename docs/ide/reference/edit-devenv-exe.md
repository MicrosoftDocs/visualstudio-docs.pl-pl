---
title: -Edit (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Edit Devenv switch
- Devenv, /Edit switch
- /Edit Devenv switch
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f0eb7cab3b1bc764f663cd647811928510281e8
ms.sourcegitcommit: ba5e072c9fedeff625a1332f22dcf3644d019f51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66432013"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)

Otwiera określony plik w istniejącego wystąpienia programu Visual Studio.

## <a name="syntax"></a>Składnia

```shell
devenv /Edit [File1[ FileN]...]
```

## <a name="arguments"></a>Argumenty

- *File1*

  Opcjonalna. Plik można otworzyć w istniejącego wystąpienia programu Visual Studio. Jeśli nie ma wystąpień programu Visual Studio, jest tworzone nowe wystąpienie o uproszczonym układzie okna i otwarciu narzędzia *plik1* w nowym wystąpieniu.

- *FileN*

  Opcjonalna. Jeden lub więcej dodatkowych plików do otwierania w istniejącym wystąpieniu programu Visual Studio.

## <a name="remarks"></a>Uwagi

Jeśli plik nie jest określona, istniejącego wystąpienia programu Visual Studio zostanie ustawiony fokus. Jeśli jest określony plik nie istnieje żadne wystąpienie programu Visual Studio, narzędziu tworzy wystąpienie o uproszczonym układzie okna.

Jeśli stan modalny istniejącego wystąpienia programu Visual Studio, plik zostanie otwarty w istniejącym wystąpieniu gdy program Visual Studio kończy stan modalny. Na przykład, ta sytuacja może wystąpić podczas [okno dialogowe Opcje](../../ide/reference/options-dialog-box-visual-studio.md) jest otwarty.

Jeśli więcej niż jedno wystąpienie programu Visual Studio jest otwarty, plik jest otwarty w ostatnio otwieranych wystąpienia.

## <a name="example"></a>Przykład

Pierwszy przykład otwiera plik `MyFile.cs` w istniejącego wystąpienia programu Visual Studio. Jeśli nie istnieje wystąpienie programu Visual Studio, narzędziu otwiera plik w nowym wystąpieniu. Drugi przykład jest podobny, z tą różnicą, że spowoduje to otwarcie trzy pliki, a nie tylko jeden plik.

```shell
devenv /edit MyFile.cs

devenv /edit MyFile1.cs MyFile2.cs MyFile3.cs
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
