---
title: -Edit (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Edit Devenv switch
- Devenv, /Edit switch
- /Edit Devenv switch
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb5ae37d3e4dc0973320c68f9db169cdbf7d663a
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227684"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)

Otwiera określony plik w istniejącego wystąpienia programu Visual Studio.

## <a name="syntax"></a>Składnia

```shell
devenv /Edit [File1[ FileN]...]
```

## <a name="arguments"></a>Argumenty

- *Plik1*

  Opcjonalna. Plik można otworzyć w istniejącego wystąpienia programu Visual Studio. Jeśli nie ma wystąpień programu Visual Studio, jest tworzone nowe wystąpienie o uproszczonym układzie okna i otwarciu narzędzia *plik1* w nowym wystąpieniu.

- *Plikn*

  Opcjonalna. Jeden lub więcej dodatkowych plików do otwierania w istniejącym wystąpieniu programu Visual Studio.

## <a name="remarks"></a>Uwagi

Jeśli plik nie jest określona, istniejącego wystąpienia programu Visual Studio zostanie ustawiony fokus. Jeśli jest określony plik nie istnieje żadne wystąpienie programu Visual Studio, narzędziu tworzy wystąpienie o uproszczonym układzie okna.

Jeśli stan modalny istniejącego wystąpienia programu Visual Studio, plik zostanie otwarty w istniejącym wystąpieniu gdy program Visual Studio kończy stan modalny. Na przykład, ta sytuacja może wystąpić podczas [okno dialogowe Opcje](../../ide/reference/options-dialog-box-visual-studio.md) jest otwarty.

## <a name="example"></a>Przykład

Pierwszy przykład otwiera plik `MyFile.cs` w istniejącego wystąpienia programu Visual Studio. Jeśli nie istnieje wystąpienie programu Visual Studio, narzędziu otwiera plik w nowym wystąpieniu. Drugi przykład jest podobny, z tą różnicą, że spowoduje to otwarcie trzy pliki, a nie tylko jeden plik.

```shell
devenv /edit MyFile.cs

devenv /edit MyFile1.cs MyFile2.cs MyFile3.cs
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)