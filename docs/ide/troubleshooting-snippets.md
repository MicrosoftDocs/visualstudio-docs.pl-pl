---
title: Rozwiązywanie problemów z fragmentami kodu
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75b6c18c5d12d4d39d9025de2ed51cd15c8dda82
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647526"
---
# <a name="troubleshoot-snippets"></a>Rozwiązywanie problemów z fragmentami kodu

Problemy ze fragmentami kodu IntelliSense są zwykle spowodowane przez dwa problemy: uszkodzony plik fragmentu lub zła zawartość w pliku fragmentu.

## <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Nie można przeciągnąć fragmentu z Eksploratora plików do pliku źródłowego programu Visual Studio

- KOD XML w pliku fragmentu kodu może być uszkodzony. **Edytor XML** w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] może lokalizować problemy w strukturze XML.

- Plik fragmentu kodu może nie być zgodny ze schematem fragmentu kodu. **Edytor XML** w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] może lokalizować problemy w strukturze XML.

## <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Kod zawiera błędy kompilatora, które nie są wyróżnione

- Brak odwołania do projektu. Zapoznaj się z dokumentacją dotyczącą fragmentu kodu. Jeśli na komputerze nie znaleziono odwołania, należy je zainstalować. Wstawianie fragmentu kodu powinno dodać do projektu wszystkie potrzebne odwołania. Jeśli fragment kodu nie zawiera informacji referencyjnych, które mogą zostać zgłoszone do twórcy fragmentu jako błąd.

- Zmienna może być niezdefiniowana. Niezdefiniowane zmienne w fragmencie kodu powinny być wyróżnione. Jeśli nie, to można zgłosić do twórcy fragmentu kodu jako błąd.

## <a name="see-also"></a>Zobacz także

- [Fragmenty kodu](../ide/code-snippets.md)
