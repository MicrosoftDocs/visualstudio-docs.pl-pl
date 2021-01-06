---
title: Wyświetl informacje śledzenia WPF | Microsoft Docs
description: Program Visual Studio może odbierać informacje o śledzeniu debugowania z aplikacji WPF i wyświetlać je w oknie danych wyjściowych. Dowiedz się, jak zarządzać śledzeniem WPF i dostosowywać je.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e4800c2ca44c2c52b2059685d9c5bc4fe38ed08
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903977"
---
# <a name="how-to-display-wpf-trace-information"></a>Porady: wyświetlanie informacji o śledzeniu WPF
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] może odbierać informacje o śledzeniu debugowania z aplikacji WPF i wyświetlać te informacje w oknie **danych wyjściowych** . Aby wyświetlić informacje o śledzeniu debugowania, należy włączyć śledzenie WPF.

 Śledzenie WPF można włączyć w pliku App.Config lub programowo przy użyciu <xref:System.Diagnostics.PresentationTraceSources> klasy. Łatwiejszym sposobem włączenia śledzenia WPF jest użycie okna **Opcje** . Śledzenie WPF dla aplikacji sieci Web nie jest obsługiwane.

### <a name="to-enable-or-customize-wpf-trace-information"></a>Aby włączyć lub dostosować informacje śledzenia WPF

1. W menu **Tools** (Narzędzia) wybierz pozycję **Options** (Opcje).

2. W oknie dialogowym **Opcje** , w polu po lewej stronie Otwórz węzeł **debugowanie** .

3. W obszarze **debugowanie** kliknij **okno dane wyjściowe**.

4. W obszarze **Ogólne ustawienia danych wyjściowych** wybierz pozycję **wszystkie dane wyjściowe debugowania**.

5. W polu po prawej stronie Znajdź pozycję **ustawienia śledzenia WPF**.

6. Otwórz węzeł **ustawienia śledzenia WPF** .

7. W obszarze **ustawienia śledzenia WPF** kliknij kategorię ustawień, które chcesz włączyć (na przykład **powiązanie danych**).

     Kontrolka listy rozwijanej jest wyświetlana w kolumnie ustawienia obok pozycji **powiązanie danych** lub niezależnie od wybranej kategorii.

8. Kliknij listę rozwijaną i wybierz typ informacji śledzenia, które chcesz wyświetlić: **wszystkie**, **krytyczne**, **błąd**, **Ostrzeżenie**, **informacje**, **pełne** lub **ActivityTracing**.

     **Krytyczne** umożliwia śledzenie tylko zdarzeń krytycznych.

     **Błąd** umożliwia śledzenie zdarzeń krytycznych i błędów.

     **Ostrzeżenie** umożliwia śledzenie zdarzeń krytycznych, błędów i ostrzeżeń.

     **Informacje** umożliwiają śledzenie zdarzeń krytycznych, błędów, ostrzeżeń i informacji.

     Funkcja **verbose** umożliwia śledzenie zdarzeń krytycznych, błędów, ostrzeżeń, informacji i pełnych.

     **ActivityTracing** umożliwia śledzenie zdarzeń zatrzymania, uruchamiania, zawieszania, przesyłania i wznawiania.

     Aby uzyskać więcej informacji na temat tego, co oznaczają te poziomy informacji o śledzeniu, zobacz <xref:System.Diagnostics.SourceLevels> .

9. Kliknij przycisk **OK**.

### <a name="to-disable-wpf-trace-information"></a>Aby wyłączyć informacje śledzenia WPF

1. W menu **Tools** (Narzędzia) wybierz pozycję **Options** (Opcje).

2. W oknie dialogowym **Opcje** , w polu po lewej stronie Otwórz węzeł **debugowanie** .

3. W obszarze **debugowanie** kliknij **okno dane wyjściowe**.

4. W polu po prawej stronie Znajdź pozycję **ustawienia śledzenia WPF**.

5. Otwórz węzeł **ustawienia śledzenia WPF** .

6. W obszarze **ustawienia śledzenia WPF** kliknij kategorię ustawień, które chcesz włączyć (na przykład **powiązanie danych**).

     Kontrolka listy rozwijanej jest wyświetlana w kolumnie ustawienia obok pozycji **powiązanie danych** lub niezależnie od wybranej kategorii.

7. Kliknij listę rozwijaną i wybierz pozycję **wyłączone**.

8. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też
- [Debugowanie WPF](../debugger/debugging-wpf.md)