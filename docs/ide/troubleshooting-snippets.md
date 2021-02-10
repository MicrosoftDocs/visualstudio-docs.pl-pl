---
title: Rozwiązywanie problemów z fragmentami kodu
description: Dowiedz się, jak rozwiązywać problemy ze fragmentami kodu IntelliSense, które zwykle są spowodowane przez złą zawartość pliku fragmentu lub uszkodzonego pliku fragmentu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d18e65fe14d231fa7cc9ea515eddaf89fc5c2b81
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971482"
---
# <a name="troubleshoot-snippets"></a>Rozwiązywanie problemów z fragmentami kodu

Problemy ze fragmentami kodu IntelliSense są zwykle spowodowane przez dwa problemy: uszkodzony plik fragmentu lub zła zawartość w pliku fragmentu.

## <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Nie można przeciągnąć fragmentu z Eksploratora plików do pliku źródłowego programu Visual Studio

- KOD XML w pliku fragmentu kodu może być uszkodzony. **Edytor XML** w programie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] może lokalizować problemy w strukturze XML.

- Plik fragmentu kodu może nie być zgodny ze schematem fragmentu kodu. **Edytor XML** w programie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] może lokalizować problemy w strukturze XML.

## <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Kod zawiera błędy kompilatora, które nie są wyróżnione

- Brak odwołania do projektu. Zapoznaj się z dokumentacją dotyczącą fragmentu kodu. Jeśli na komputerze nie znaleziono odwołania, należy je zainstalować. Wstawianie fragmentu kodu powinno dodać do projektu wszystkie potrzebne odwołania. Jeśli fragment kodu nie zawiera informacji referencyjnych, które mogą zostać zgłoszone do twórcy fragmentu jako błąd.

- Zmienna może być niezdefiniowana. Niezdefiniowane zmienne w fragmencie kodu powinny być wyróżnione. Jeśli nie, to można zgłosić do twórcy fragmentu kodu jako błąd.

## <a name="see-also"></a>Zobacz też

- [Fragmenty kodu](../ide/code-snippets.md)
