---
title: Import i eksport ustawień — polecenie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e3ee8549fd8cf1a4551818c013551ba24128f95
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671051"
---
# <a name="import-and-export-settings-command"></a>Import i eksport ustawień — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Importuje, eksportuje lub resetuje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ustawień.

## <a name="syntax"></a>Składnia

```
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Przełączniki
 /Export: `filename` opcjonalny. Eksportuje bieżące ustawienia do określonego pliku.

 /import: `filename` opcjonalny. Importuje ustawienia w określonym pliku.

 /Reset opcjonalne. Resetuje bieżące ustawienia.

## <a name="remarks"></a>Uwagi
 Uruchomienie tego polecenia bez przełączników powoduje otwarcie kreatora **importowania i eksportowania ustawień** . Aby uzyskać więcej informacji, zobacz [jak: udostępnianie ustawień między komputerami lub wersjami programu Visual Studio](https://msdn.microsoft.com/1131fb10-35c1-42da-9cd8-91aa3235b882).

## <a name="example"></a>Przykład
 Następujące polecenie eksportuje ustawienia bieżący do pliku `MyFile.vssettings`.

```
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Zobacz też
 [Dostosowywanie ustawień programistycznych w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
