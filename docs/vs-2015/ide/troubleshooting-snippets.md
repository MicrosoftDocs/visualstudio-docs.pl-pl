---
title: Fragmenty kodu rozwiązywania problemów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f73cb7ba59daf2f8ee957d95dee36bba59f87614
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654780"
---
# <a name="troubleshooting-snippets"></a>Rozwiązywanie problemów z wstawkami kodu programu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Problemy ze fragmentami kodu IntelliSense są zwykle spowodowane przez dwa problemy: uszkodzony plik fragmentu lub zła zawartość w pliku fragmentu.

## <a name="common-problems"></a>Typowe problemy

### <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Nie można przeciągnąć fragmentu z Eksploratora plików do pliku źródłowego programu Visual Studio

- KOD XML w pliku fragmentu kodu może być uszkodzony. **Edytor XML** w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] może lokalizować problemy w strukturze XML.

- Plik fragmentu kodu może nie być zgodny ze schematem fragmentu kodu. **Edytor XML** w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] może lokalizować problemy w strukturze XML.

### <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Kod zawiera błędy kompilatora, które nie są wyróżnione

- Brak odwołania do projektu. Zapoznaj się z dokumentacją dotyczącą fragmentu kodu. Jeśli na komputerze nie znaleziono odwołania, należy je zainstalować. Wstawianie fragmentu kodu powinno dodać do projektu wszystkie potrzebne odwołania. Jeśli fragment kodu nie zawiera informacji referencyjnych, które mogą zostać zgłoszone do twórcy fragmentu jako błąd.

- Zmienna może być niezdefiniowana. Niezdefiniowane zmienne w fragmencie kodu powinny być wyróżnione. Jeśli nie, to można zgłosić do twórcy fragmentu kodu jako błąd.

## <a name="see-also"></a>Zobacz też
 [Fragmenty kodu](../ide/code-snippets.md)
