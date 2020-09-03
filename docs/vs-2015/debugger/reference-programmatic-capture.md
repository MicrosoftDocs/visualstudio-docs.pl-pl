---
title: Odwołanie (przechwycenie programowe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8cebeb7eb651c11b5f560b981df30213fc726c66
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162259"
---
# <a name="reference-programmatic-capture"></a>Odwołanie (przechwycenie programowe)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diagnostyka grafiki obsługuje kontrolę programistyczną nad jej funkcjami przechwytywania za pośrednictwem interfejsu API przechwytywania programowego. Za pomocą tego interfejsu API można przełączać i dodawać komunikaty do HUD diagnostyki grafiki (na potrzeby wyświetlania), inicjować i tworzyć pliki dzienników grafiki, a także przechwytywać informacje graficzne.  
  
## <a name="programmatic-capture-apis"></a>Interfejsy API przechwytywania programistycznego  
  
### <a name="classes"></a>Klasy  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[VsgDbg — Klasa](../debugger/vsgdbg-class.md)|Reprezentuje interfejs, za pomocą którego składnik aplikacji diagnostyki grafiki jest kontrolowany programowo.|  
  
### <a name="preprocessor-symbols"></a>Symbole preprocesora  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)|Określa, czy plik dziennika grafiki jest zapisywany w katalogu plików tymczasowych użytkownika.|  
|[VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)|Określa domyślną nazwę pliku dziennika grafiki.|  
|[VSG_NODEFAULT_INSTANCE](../debugger/vsg-nodefault-instance.md)|Określa, czy `VsgDbg` jest udostępniane wystąpienie domyślne klasy.|  
  
## <a name="related-articles"></a>Powiązane artykuły  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Przechwytywanie informacji graficznych](../debugger/capturing-graphics-information.md)|Pokazuje, jak przechwytywać informacje graficzne z aplikacji opartej na technologii DirectX, dzięki czemu można używać [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzi Diagnostyka grafiki do diagnozowania problemów z renderowaniem.|  
|[Omówienie](../debugger/overview-of-visual-studio-graphics-diagnostics.md)|Pokazuje, w jaki sposób Diagnostyka grafiki może pomóc w debugowaniu błędów renderowania w grach i aplikacjach DirectX.|
