---
title: Odwołanie (przechwytywanie programowe) | Microsoft Docs
description: Interfejs API przechwytywania programowego umożliwia kontrolowanie programowej kontroli nad funkcjami przechwytywania Diagnostyka grafiki.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 572629235e3b64028b70ff59090f9c4f7991d323
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232703"
---
# <a name="reference-programmatic-capture"></a>Odwołanie (przechwycenie programowe)
Diagnostyka grafiki obsługuje programowe sterowanie funkcjami przechwytywania za pośrednictwem interfejsu API przechwytywania programowego. Za pomocą tego interfejsu API można przełączać i dodawać komunikaty do graficznego ekranu hud diagnostyki (Head-Up Display), inicjować i tworzyć pliki dziennika grafiki oraz przechwytywać informacje graficzne.

## <a name="programmatic-capture-apis"></a>Programowe interfejsy API przechwytywania

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|----------|-----------------|
|[VsgDbg — Klasa](vsgdbg-class.md)|Reprezentuje interfejs, za pomocą którego składnik diagnostyki grafiki w aplikacji jest kontrolowany programowo.|

### <a name="preprocessor-symbols"></a>Symbole preprocesora

|Nazwa|Opis|
|----------|-----------------|
|[DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)|Określa, czy plik dziennika grafiki jest zapisywany w katalogu plików tymczasowych użytkownika.|
|[VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)|Definiuje domyślną nazwę pliku dziennika grafiki.|
|[VSG_NODEFAULT_INSTANCE](vsg-nodefault-instance.md)|Definiuje według obecności, czy jest udostępniane domyślne `VsgDbg` wystąpienie klasy.|

## <a name="related-articles"></a>Powiązane artykuły

| Tytuł | Opis |
| - | - |
| [Przechwytywanie informacji graficznych](capturing-graphics-information.md) | Przedstawia sposób przechwytywania informacji graficznych z aplikacji opartej na directx, dzięki czemu można używać [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] narzędzi Diagnostyka grafiki do diagnozowania problemów z renderowaniem. |
| [Omówienie](overview-of-visual-studio-graphics-diagnostics.md) | Pokazuje, Diagnostyka grafiki mogą pomóc w debugowaniu błędów renderowania w aplikacjach i gier DirectX. |
