---
title: Parametry połączenia zawierają poświadczenia z hasłem w postaci zwykłego tekstu i nie korzystają ze zintegrowanych zabezpieczeń
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 0a8cb18e84263d7b7144764d007a2928956fc77b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72641026"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>Parametry połączenia zawierają poświadczenia z hasłem w postaci zwykłego tekstu i nie korzystają ze zintegrowanych zabezpieczeń

Czy chcesz zapisać parametry połączenia w bieżącym pliku DBML i plikach konfiguracji aplikacji z tymi informacjami poufnymi?  Kliknij przycisk **nie** , aby zapisać parametry połączenia bez informacji poufnych.

Podczas pracy z połączeniami danych zawierającymi informacje poufne (hasła zawarte w parametrach połączenia) można zapisać parametry połączenia w pliku DBML projektu i pliku konfiguracji aplikacji z lub bez informacje poufne.

> [!WARNING]
> Jawne ustawienie właściwości **połączenia** właściwości **ustawień aplikacji** na **Fałsz** spowoduje dodanie hasła do pliku DBML.

## <a name="save-options"></a>Opcje zapisywania

- Aby zapisać parametry połączenia z informacjami poufnymi, wybierz opcję **tak**.

   Parametry połączenia są przechowywane jako ustawienia aplikacji. Parametry połączenia zawierają informacje poufne w postaci zwykłego tekstu. Plik DBML nie zawiera informacji poufnych.

- Aby zapisać parametry połączenia bez informacji poufnych, wybierz pozycję **nie**.

   Parametry połączenia są przechowywane jako ustawienia aplikacji, ale hasło nie jest uwzględniane.

## <a name="see-also"></a>Zobacz także

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)