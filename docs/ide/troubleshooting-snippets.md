---
title: Rozwiązywanie problemów z fragmentami kodu
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9485147bbe386983aa5ee9c492607e12afb151c6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60080952"
---
# <a name="troubleshoot-snippets"></a>Rozwiązywanie problemów z fragmentami kodu

Problemy z fragmenty kodu IntelliSense są zazwyczaj spowodowane dwa problemy: plik fragmentu w uszkodzona lub zły zawartość pliku fragmentu kodu.

## <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Fragment kodu nie można przeciągnąć z Eksploratora plików do pliku źródłowego programu Visual Studio

- Kod XML w pliku fragmentu kodu może być uszkodzony. **Edytora XML** w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mogą zlokalizować problemów w strukturze XML.

- Plik fragmentu kodu nie może być zgodny ze schematem fragmentu kodu. **Edytora XML** w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mogą zlokalizować problemów w strukturze XML.

## <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Kod ma błędy kompilatora, które nie są wyróżnione

- Być może brakuje odwołania projektu. Sprawdź dokumentację dotyczącą fragmentu kodu. Odwołanie nie zostanie znaleziony na komputerze, należy go zainstalować. Wstawianie fragmentu należy dodać do projektu wszystkie odwołania potrzebne. Jeżeli ten fragment kodu brakuje zawiera informacje, które mogą zostać zgłoszone do autora fragmentu kodu jako błąd.

- Zmienna może być niezdefiniowana. Powinien być wyróżniony niezdefiniowane zmienne we fragmencie. Jeśli nie, które mogą zostać zgłoszone do autora fragmentu kodu jako błąd.

## <a name="see-also"></a>Zobacz także

- [Fragmenty kodu](../ide/code-snippets.md)
