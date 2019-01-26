---
title: Odwołanie (przechwycenie programowe) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 892831423ccc3607db1b3f162fb79f4508764afa
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006754"
---
# <a name="reference-programmatic-capture"></a>Odwołanie (przechwycenie programowe)
Graphics Diagnostics obsługuje programowe kontrolę nad jego funkcji przechwytywania przy użyciu Przechwytywanie programistyczne interfejsu API. Ten interfejs API umożliwia Przełącz i dodawanie komunikatów do diagnostyki grafiki HUD (wyświetlanie Head telefoniczny), inicjowanie i tworzyć pliki dziennika grafiki i przechwytywać informacje graficzne.  

## <a name="programmatic-capture-apis"></a>Przechwytywanie programistyczne interfejsy API  

### <a name="classes"></a>Klasy  

|Nazwa|Opis|  
|----------|-----------------|  
|[VsgDbg, klasa](vsgdbg-class.md)|Reprezentuje interfejs, za pomocą którego składnik w aplikacji diagnostyki grafiki jest kontrolowany programowo.|  

### <a name="preprocessor-symbols"></a>Symboli preprocesora  

|Nazwa|Opis|  
|----------|-----------------|  
|[DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)|Definiuje jego obecność czy plik dziennika grafiki jest zapisywany do katalogu plików tymczasowych użytkownika.|  
|[VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)|Definiuje domyślną nazwę pliku pliku dziennika grafiki.|  
|[VSG_NODEFAULT_INSTANCE](vsg-nodefault-instance.md)|Definiuje przez jego obecność, czy domyślne wystąpienie `VsgDbg` są dostarczane przez klasy.|  

## <a name="related-articles"></a>Powiązane artykuły  

| Tytuł | Opis |
| - | - |
| [Przechwytywanie informacji graficznych](capturing-graphics-information.md) | Pokazuje, jak przechwytywać informacje graficzne z aplikacji opartej na DirectX, tak aby można było używać [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] narzędziami diagnostyki grafiki do diagnozowania problemów z renderowaniem. |
| [Omówienie](overview-of-visual-studio-graphics-diagnostics.md) | Pokazuje, jak Graphics Diagnostics można debugować błędy renderowania w grach i aplikacjach DirectX. |
