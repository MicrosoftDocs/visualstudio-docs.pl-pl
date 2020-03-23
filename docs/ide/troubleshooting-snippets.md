---
title: Rozwiązywanie problemów z fragmentami kodu
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a699c6a158b5a0751824c7634ddd637467da50d2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588697"
---
# <a name="troubleshoot-snippets"></a>Rozwiązywanie problemów z fragmentami kodu

Problemy ze fragmentami kodu IntelliSense są zazwyczaj spowodowane przez dwa problemy: uszkodzony plik fragmentu kodu lub złą zawartość w pliku urywka.

## <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Nie można przeciągnąć fragmentu kodu z Eksploratora plików do pliku źródłowego programu Visual Studio

- Kod XML w pliku urywka może być uszkodzony. **Edytor XML** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] w może zlokalizować problemy w strukturze XML.

- Plik urywka może nie być zgodny ze schematem fragmentu kodu. **Edytor XML** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] w może zlokalizować problemy w strukturze XML.

## <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Kod zawiera błędy kompilatora, które nie są wyróżnione

- Może brakować odwołania do projektu. Sprawdź dokumentację dotyczącą fragmentu kodu. Jeśli odwołanie nie zostanie znalezione na komputerze, należy je zainstalować. Wstawianie fragmentu kodu należy dodać do projektu wszelkie odwołania potrzebne. Jeśli fragment kodu brakuje informacji referencyjnych, które mogą być zgłaszane do twórcy fragmentu kodu jako błąd.

- Zmienna może być niezdefiniowana. Niezdefiniowane zmienne we urywku powinny być wyróżnione. Jeśli nie, można to zgłosić twórcy urywka jako błąd.

## <a name="see-also"></a>Zobacz też

- [Fragmenty kodu](../ide/code-snippets.md)
