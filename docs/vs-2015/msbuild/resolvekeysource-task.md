---
title: ResolveKeySource — — zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveKeySource task [MSBuild]
- MSBuild, ResolveKeySource task
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bd5cbe2f4998ab78ce39cde4b26a38b13c70b2f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193722"
---
# <a name="resolvekeysource-task"></a>ResolveKeySource — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa źródło klucza o silnej nazwie.  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry `ResolveKeySource` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AutoClosePasswordPromptShow`|Opcjonalny `Int32` parametr.<br /><br /> Pobiera lub ustawia czas (w sekundach) wyświetlania komunikatu o pomniejszeniu.|  
|`AutoClosePasswordPromptTimeout`|Opcjonalny `Int32` parametr.<br /><br /> Pobiera lub ustawia czas (w sekundach) oczekiwania przed zamknięciem okna dialogowego monitu o hasło.|  
|`CertificateFile`|Opcjonalny `String` parametr.<br /><br /> Pobiera lub ustawia ścieżkę pliku certyfikatu.|  
|`CertificateThumbprint`|Opcjonalny `String` parametr.<br /><br /> Pobiera lub ustawia odcisk palca certyfikatu.|  
|`KeyFile`|Opcjonalny `String` parametr.<br /><br /> Pobiera lub ustawia ścieżkę pliku klucza.|  
|`ResolvedKeyContainer`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Pobiera lub ustawia rozpoznany kontener kluczy.|  
|`ResolvedKeyFile`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Pobiera lub ustawia rozpoznany plik klucza.|  
|`ResolvedThumbprint`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Pobiera lub ustawia odcisk palca rozpoznanego certyfikatu.|  
|`ShowImportDialogDespitePreviousFailures`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , Pokaż okno dialogowe importowania pomimo poprzednich błędów.|  
|`SuppressAutoClosePasswordPrompt`|Opcjonalny `Boolean` parametr.<br /><br /> Pobiera lub ustawia wartość logiczną określającą, czy okno dialogowe monitu o hasło nie powinno być autozamykane.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
