---
title: 'Instrukcje: Włącz pluralizacja włączać i wyłączać (Projektant O-R) | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a446e91095d9498a6182d1f80d046382b64e876e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63384303"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Instrukcje: Pluralizacja Włączanie i wyłączanie (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Domyślnie podczas przeciągania obiektów bazy danych, które mają nazwy kończące się na s lub ię od **Eksploratora serwera**/**Eksplorator bazy danych** na [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), nazwy wygenerowanych klas jednostek zostaną zmienione w liczbie mnogiej na liczbę pojedynczą. W ten sposób bardziej przedstawiać fakt, że klasa wystąpień jednostki mapowany na pojedynczy rekord danych. Na przykład dodanie tabeli Customers [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] wyniki w klasie jednostki o nazwie odbiorcy, ponieważ klasa przechowuje dane dla jednego klienta.  
  
> [!NOTE]
> Pluralizacja jest domyślnie tylko w języku angielskim wersji programu Visual Studio.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-turn-pluralization-on-and-off"></a>Aby włączyć pluralizacja włączać i wyłączać  
  
1. Na **narzędzia** menu, kliknij przycisk **opcje**.  
  
2. W **opcje** okna dialogowego rozwiń **narzędzia graficzne bazy danych**.  
  
> [!NOTE]
> Wybierz **Pokaż wszystkie ustawienia** Jeśli **narzędzia graficzne bazy danych** węzeł nie jest widoczny.  
  
1. Kliknij przycisk **O/R Designer**.  
  
2. Ustaw **Pluralizację nazw** do **włączone** = **False** można ustawić [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] tak, aby nie zmienia nazwy klas.  
  
3. Ustaw **Pluralizację nazw** do **włączone** = **True** mają dotyczyć zasady pluralizacja nazw klasy obiekty dodane do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ do SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
