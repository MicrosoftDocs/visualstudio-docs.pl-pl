---
title: Odwołanie (przechwycenie programowe) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 66e80d02ac41d78f2c79e7b2accb11388d456ad8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51744272"
---
# <a name="reference-programmatic-capture"></a>Odwołanie (przechwycenie programowe)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Graphics Diagnostics obsługuje programowe kontrolę nad jego funkcji przechwytywania przy użyciu Przechwytywanie programistyczne interfejsu API. Ten interfejs API umożliwia Przełącz i dodawanie komunikatów do diagnostyki grafiki HUD (wyświetlanie Head telefoniczny), inicjowanie i tworzyć pliki dziennika grafiki i przechwytywać informacje graficzne.  
  
## <a name="programmatic-capture-apis"></a>Przechwytywanie programistyczne interfejsy API  
  
### <a name="classes"></a>Klasy  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[VsgDbg, klasa](../debugger/vsgdbg-class.md)|Reprezentuje interfejs, za pomocą którego składnik w aplikacji diagnostyki grafiki jest kontrolowany programowo.|  
  
### <a name="preprocessor-symbols"></a>Symboli preprocesora  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)|Definiuje jego obecność czy plik dziennika grafiki jest zapisywany do katalogu plików tymczasowych użytkownika.|  
|[VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)|Definiuje domyślną nazwę pliku pliku dziennika grafiki.|  
|[VSG_NODEFAULT_INSTANCE](../debugger/vsg-nodefault-instance.md)|Definiuje przez jego obecność, czy domyślne wystąpienie `VsgDbg` są dostarczane przez klasy.|  
  
## <a name="related-articles"></a>Powiązane artykuły  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Przechwytywanie informacji graficznych](../debugger/capturing-graphics-information.md)|Pokazuje, jak przechwytywać informacje graficzne z aplikacji opartej na DirectX, tak aby można było używać [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędziami diagnostyki grafiki do diagnozowania problemów z renderowaniem.|  
|[Omówienie](../debugger/overview-of-visual-studio-graphics-diagnostics.md)|Pokazuje, jak Graphics Diagnostics można debugować błędy renderowania w grach i aplikacjach DirectX.|



