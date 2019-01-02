---
title: Obsługa wątkowości w Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- multiple threads [Office development in Visual Studio]
- threading [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], threading support
- object models [Office development in Visual Studio], threading support
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 48a7ab96b26dc9410eef6977c53af7a3cf4a9841
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857896"
---
# <a name="threading-support-in-office"></a>Obsługa wątkowości w Office
  Ten artykuł zawiera informacje dotyczące sposobu wątkowości jest obsługiwana w modelu obiektów programu Microsoft Office. Model obiektów programu pakietu Office nie jest bezpieczny dla wątków, ale można pracować z wieloma wątkami w rozwiązań pakietu Office. Aplikacje pakietu Office są serwery Component Object Model (COM). COM umożliwia klientom wywoływanie serwerów COM na dowolnych wątków. W przypadku serwerów COM, które nie są bezpieczne dla wątków COM zapewnia mechanizm serializacji współbieżnych wywołań, tak aby tylko jeden wątek logicznych jest wykonywana na serwerze w dowolnym momencie. Ten mechanizm jest określany jako model apartamentem jednowątkowym (przedziale STA). Ponieważ wywołania są serializowane, wywołań może być blokowany przez czas, gdy serwer jest zajęty lub obsługuje inne wywołania w wątku tła.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="knowledge-required-when-using-multiple-threads"></a>Wymagana wiedza, korzystając z wielu wątków  
 Aby pracować z wielu wątków, musi mieć co najmniej podstawową wiedzę na temat następujących aspektów wielowątkowość:  
  
- Windows API  
  
- COM pojęcia wielowątkowe  
  
- Współbieżność  
  
- Synchronizacja  
  
- marshaling  
  
  Aby uzyskać ogólne informacje o wielowątkowości, zobacz [zarządzana wątkowość](/dotnet/standard/threading/).  
  
  Office działa w komórce jednowątkowej głównego Zrozumienia konsekwencji tego umożliwia zrozumienie, jak wiele wątków za pomocą pakietu Office.  
  
## <a name="basic-multithreading-scenario"></a>Podstawowy scenariusz wielowątkowości  
 Kod w rozwiązaniach pakietu Office jest zawsze uruchamiany w głównym wątku interfejsu użytkownika. Możesz chcieć wygładzania nagłych wydajność aplikacji, uruchamiając oddzielne zadanie w wątku tła. Celem jest wykonać dwie czynności pozornie jednocześnie zamiast jednego zadania następuje z drugiej strony, co powinno spowodować wykonanie gładsze (głównym celem użycia wielu wątków). Na przykład Niewykluczone, że kod zdarzenia w głównym wątku interfejsu użytkownika programu Excel, a w wątku w tle mogą uruchomić zadanie, które zbiera dane z serwera i aktualizuje komórek w Interfejsie użytkownika programu Excel przy użyciu danych z serwera.  
  
## <a name="background-threads-that-call-into-the-office-object-model"></a>Wątków w tle, które wywołują modelu obiektów pakietu Office  
 Gdy wątku w tle wywołuje aplikacji pakietu Office, wywołanie jest automatycznie organizowane przez granicę STA. Jednak nie ma żadnej gwarancji, że aplikacji pakietu Office może obsłużyć wywołania w czasie wątku w tle powoduje, że jej. Istnieje kilka możliwości:  
  
1. Aplikacja pakietu Office muszą pompy komunikatów do wywołania mieć możliwość wprowadzenia. Jeśli wykonywanie operacji może potrwać obciążenie przetwarzania bez otrzymania to.  
  
2. Jeśli inny wątek logicznej jest już apartament, nie można wprowadzić nowy wątek. Dzieje się tak często, gdy logiczne wątku przechodzi z aplikacji pakietu Office, a następnie udostępnia współużytkowane wywołanie apartamentu obiektu wywołującego. Aplikacja została zablokowana, oczekiwanie na wywołania do zwrócenia.  
  
3. Program Excel może być w stanie w taki sposób, że połączenie nie może obsługiwać natychmiast. Na przykład aplikacji pakietu Office może wyświetlanie modalne okno dialogowe.  
  
   Możliwości, 2 i 3, zapewnia COM [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter) interfejsu. Jeśli serwer implementuje go, wszystkie wywołania wprowadź za pośrednictwem [HandleIncomingCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-handleincomingcall) metody. Możliwości 2 wywołania są automatycznie odrzucane. Możliwości 3 serwer może odrzucić wywołanie, w zależności od okoliczności. Jeśli wywołanie zostanie odrzucone, obiekt wywołujący należy zdecydować, co należy zrobić. Zwykle implementuje obiekt wywołujący [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter), w którym to przypadku będą otrzymywać powiadomienia o odrzucenie przez [RetryRejectedCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-retryrejectedcall) metody.  
  
   Jednak w przypadku rozwiązania utworzone przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio, Usługa międzyoperacyjna modelu COM konwertuje wszystkie odrzucone wywołania <xref:System.Runtime.InteropServices.COMException> ("Filtr komunikatu wskazuje że aplikacja jest zajęta"). Zawsze, gdy należy wywołać model obiektu na wątku w tle muszą być gotowi do obsługi tego wyjątku. Zazwyczaj, który obejmuje podejmowaniu prób przez pewien czas, a następnie wyświetlając okna dialogowego. Jednak można również utworzyć wątku w tle jako STA, a następnie zarejestrować filtr komunikatu dla tego wątku do obsługi tej sprawy.  
  
## <a name="start-the-thread-correctly"></a>Poprawne uruchomienie wątku  
 Podczas tworzenia nowego wątku STA. Ustaw stan apartamentu STA przed rozpoczęciem korzystania z wątku. Poniższy przykład kodu pokazuje, jak to zrobić.  
  
 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]  
  
 Aby uzyskać więcej informacji, zobacz [zarządzana wątkowość — najlepsze rozwiązania](/dotnet/standard/threading/managed-threading-best-practices).  
  
## <a name="modeless-forms"></a>Niemodalne formularze  
 Niemodalne formularza umożliwia pewien rodzaj interakcji z aplikacją, gdy zostanie wyświetlony formularz. Użytkownik wchodzi w interakcję z formularzem, a formularz wchodzi w interakcję z aplikacją, bez zamknięcia. Model obiektów programu pakietu Office obsługuje niemodalne formularze zarządzanych; jednak ich nie stosuje się w wątku tła.  
  
## <a name="see-also"></a>Zobacz także  
 [Zarządzana wątkowość](/dotnet/standard/threading/)  
 [Wątkowość (C#)](/dotnet/csharp/programming-guide/concepts/threading/index) [wątkowość (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)   
 [Użyj wątki i wątkowość](/dotnet/standard/threading/using-threads-and-threading)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)  
