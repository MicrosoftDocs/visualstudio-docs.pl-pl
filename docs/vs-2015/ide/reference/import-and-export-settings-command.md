---
title: Import i eksport ustawień polecenie | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 91b34183e36c86290c14e3da7d17687d45cfe180
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694657"
---
# <a name="import-and-export-settings-command"></a>Import i eksport ustawień — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Importuje, eksportuje lub resetuje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ustawienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]  
```  
  
## <a name="switches"></a>Przełączniki  
 / export:`filename`  
 Opcjonalna. Eksportuje bieżące ustawienia do określonego pliku.  
  
 Import:`filename`  
 Opcjonalna. Importuje ustawienia w określonym pliku.  
  
 /reset  
 Opcjonalna. Przywraca bieżące ustawienia.  
  
## <a name="remarks"></a>Uwagi  
 Uruchomienie tego polecenia, na których nie zmienia otwiera **Import i eksport ustawień** kreatora. Aby uzyskać więcej informacji, zobacz [jak: Udostępnianie ustawień pomiędzy komputerami lub wersjami programu Visual Studio](https://msdn.microsoft.com/1131fb10-35c1-42da-9cd8-91aa3235b882).  
  
## <a name="example"></a>Przykład  
 Następujące polecenie eksportuje bieżące ustawienia do pliku `MyFile.vssettings`.  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie ustawień środowiska deweloperskiego w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
