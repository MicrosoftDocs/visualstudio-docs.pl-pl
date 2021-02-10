---
title: 'Instrukcje: aktualizowanie rozszerzenia programu Visual Studio | Microsoft Docs'
description: Dowiedz się, jak zaktualizować rozszerzenie programu Visual Studio w systemie przy użyciu rozszerzeń i aktualizacji w celu zainstalowania zaktualizowanej wersji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a79944fbb558e3e7a5debcfc6a64fe4b75aeb0c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946842"
---
# <a name="how-to-update-a-visual-studio-extension"></a>Instrukcje: aktualizowanie rozszerzenia programu Visual Studio
Rozszerzenie programu Visual Studio można zaktualizować w systemie przy użyciu **rozszerzeń i aktualizacji** w celu zainstalowania zaktualizowanej wersji. Jeśli utworzysz zaktualizowaną wersję rozszerzenia, możesz oznaczać ją jako zaktualizowaną przez zwiększenie numeru wersji w manifeście VSIX.

 Aktualizacje są instalowane, gdy manifest VSIX rozszerzenia przychodzącego ma taką samą wartość `ID` jak zainstalowany i wyższy `Version` numer. Jeśli `Version` liczba jest taka sama lub niższa, nie można zainstalować pakietu. Jeśli `ID` wartości nie są zgodne, pakiet, który nie jest jeszcze zainstalowany, jest rozpoznawany jako osobne rozszerzenie.

 Aby zapobiec konfliktom podczas opracowywania, zalecamy odinstalowanie wcześniejszych wersji rozszerzeń w toku, a także odinstalowanie lub wyłączenie wszelkich innych rozszerzeń, które mogą powodować konflikt.

## <a name="to-update-an-extension-on-your-system"></a>Aby zaktualizować rozszerzenie w systemie

1. W menu **Narzędzia** kliknij pozycję **Rozszerzenia i aktualizacje**.

2. W lewym okienku kliknij pozycję **aktualizacje**.

3. W środkowym okienku kliknij aktualizację, którą chcesz zainstalować.

     Numer wersji zaktualizowanego rozszerzenia jest wyświetlany w okienku po prawej stronie wraz z innymi informacjami.

4. W dolnej części okienka po prawej stronie kliknij pozycję **Aktualizuj**.

## <a name="to-publish-an-update-of-an-extension"></a>Aby opublikować aktualizację rozszerzenia

1. W programie Visual Studio Otwórz rozwiązanie dla rozszerzenia, które chcesz zaktualizować. Wprowadź zmiany.

    > [!IMPORTANT]
    > Wszystkie rozszerzenia użytkownika nie są automatycznie aktualizowane. Należy zawsze podpisywać swoje rozszerzenia.

2. W **Eksplorator rozwiązań** Otwórz plik *source. Extension. manifest*.

3. W projektancie manifestu Zwiększ wartość liczby w polu **wersja** .

4. Zapisz rozwiązanie i skompiluj je.

5. Przekaż nowy plik *VSIX* (w folderze * \bin\debug \* projektu) do witryny sieci Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) .

     Jeśli użytkownik, który ma wcześniejszą wersję rozszerzenia, otwiera **rozszerzenia i aktualizacje**, Nowa wersja zostanie wyświetlona na liście **aktualizacji** , pod warunkiem, że narzędzie jest ustawione na automatyczne wyszukiwanie aktualizacji.

     Można włączać lub wyłączać automatyczne sprawdzanie aktualizacji u dołu okienka **aktualizacje** (**Włącz/Wyłącz automatyczne wykrywanie dostępnych aktualizacji**), które zmienia ustawienie **Sprawdź dostępność aktualizacji** w obszarze Opcje **Narzędzia**  >    >    >  **rozszerzenia i aktualizacje** środowiska.

    > [!NOTE]
    > Począwszy od programu Visual Studio 2015 Update 2, można określić (w obszarze  >  **Opcje** narzędzia  >    >  **rozszerzenia i aktualizacje** środowiska), czy mają być wykonywane aktualizacje automatyczne dla rozszerzeń dla poszczególnych użytkowników, wszystkich rozszerzeń użytkowników, czy obu (ustawienie domyślne).

## <a name="see-also"></a>Zobacz też
- [Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Znajdowanie rozszerzeń programu Visual Studio i korzystanie z nich](../ide/finding-and-using-visual-studio-extensions.md)
