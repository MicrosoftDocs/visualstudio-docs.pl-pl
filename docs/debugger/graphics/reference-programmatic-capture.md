---
title: Odwołanie (przechwycenie programowe) | Microsoft Docs
description: Użyj interfejsu API przechwytywania programistycznego, aby przejąć kontrolę programistyczną dla funkcji przechwytywania Diagnostyka grafiki.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 452360e04170bbf217c2f6ac0598533f3cab2259
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905108"
---
# <a name="reference-programmatic-capture"></a>Odwołanie (przechwycenie programowe)
Diagnostyka grafiki obsługuje kontrolę programistyczną nad jej funkcjami przechwytywania za pośrednictwem interfejsu API przechwytywania programowego. Za pomocą tego interfejsu API można przełączać i dodawać komunikaty do HUD diagnostyki grafiki (na potrzeby wyświetlania), inicjować i tworzyć pliki dzienników grafiki, a także przechwytywać informacje graficzne.

## <a name="programmatic-capture-apis"></a>Interfejsy API przechwytywania programistycznego

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|----------|-----------------|
|[VsgDbg — Klasa](vsgdbg-class.md)|Reprezentuje interfejs, za pomocą którego składnik aplikacji diagnostyki grafiki jest kontrolowany programowo.|

### <a name="preprocessor-symbols"></a>Symbole preprocesora

|Nazwa|Opis|
|----------|-----------------|
|[DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)|Określa, czy plik dziennika grafiki jest zapisywany w katalogu plików tymczasowych użytkownika.|
|[VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)|Określa domyślną nazwę pliku dziennika grafiki.|
|[VSG_NODEFAULT_INSTANCE](vsg-nodefault-instance.md)|Określa, czy `VsgDbg` jest udostępniane wystąpienie domyślne klasy.|

## <a name="related-articles"></a>Powiązane artykuły

| Tytuł | Opis |
| - | - |
| [Przechwytywanie informacji graficznych](capturing-graphics-information.md) | Pokazuje, jak przechwytywać informacje graficzne z aplikacji opartej na technologii DirectX, dzięki czemu można używać [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] narzędzi Diagnostyka grafiki do diagnozowania problemów z renderowaniem. |
| [Omówienie](overview-of-visual-studio-graphics-diagnostics.md) | Pokazuje, w jaki sposób Diagnostyka grafiki może pomóc w debugowaniu błędów renderowania w grach i aplikacjach DirectX. |
