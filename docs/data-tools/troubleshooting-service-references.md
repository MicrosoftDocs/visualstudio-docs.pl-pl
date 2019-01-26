---
title: Rozwiązywanie problemów z odwołaniami usługi
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 573019483f1c7c616f8bdf61286c46f76458354f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031295"
---
# <a name="troubleshoot-service-references"></a>Rozwiązywanie problemów z odwołaniami usługi

Ten temat zawiera listę typowych problemów, które mogą wystąpić podczas pracy z Windows Communication Foundation (WCF) lub odwołania usługi danych WCF w programie Visual Studio.

## <a name="error-returning-data-from-a-service"></a>Wystąpił błąd podczas zwracania danych z usługi

Po powrocie `DataSet` lub `DataTable` z usługi, może pojawić się wyjątek "przydział maksymalny rozmiar dla komunikatów przychodzących został przekroczony". Domyślnie `MaxReceivedMessageSize` właściwość niektóre powiązania jest ustawiony na stosunkowo małej wartości, aby ograniczyć narażenie na ataki typu "odmowa usługi". Można zwiększyć tę wartość, aby zapobiec wyjątku. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A>.

Aby naprawić ten błąd:

1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie *app.config* plik, aby go otworzyć.

2.  Znajdź `MaxReceivedMessageSize` właściwości i zmień ją na większą wartość.

## <a name="cannot-find-a-service-in-my-solution"></a>Nie można odnaleźć usługi w Moje rozwiązanie

Po kliknięciu **odnajdź** znajdujący się w **Dodawanie odwołań do usług** okno dialogowe, co najmniej jeden projekt biblioteki usługi WCF w rozwiązaniu nie są wyświetlane na liście usług. Może to występować, jeśli biblioteka usług został dodany do rozwiązania, ale jeszcze nie został skompilowany.

Aby naprawić ten błąd:

-   W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt biblioteki usługi WCF i kliknij przycisk **kompilacji**.

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>Błąd podczas uzyskiwania dostępu do usługi za pośrednictwem pulpitu zdalnego

Gdy użytkownik uzyskuje dostęp do usługi WCF hostowanej w sieci Web za pośrednictwem połączenia pulpitu zdalnego i użytkownik nie ma uprawnienia administracyjne, zostanie użyte uwierzytelnianie NTLM. Jeśli użytkownik nie ma uprawnienia administracyjne, użytkownik może pojawić się następujący komunikat o błędzie: "Żądanie HTTP nie ma autoryzacji przez schemat uwierzytelniania klienta"Anonymous". Nagłówek uwierzytelnienia otrzymany z serwera była "NTLM"."

Aby naprawić ten błąd:

1.  W projekcie witryny sieci Web otwórz **właściwości** stron.

2.  Na **opcje uruchamiania** kartę, usuń zaznaczenie **uwierzytelniania NTLM** pole wyboru.

    > [!NOTE]
    > Należy wyłączyć uwierzytelnianie NTLM tylko w przypadku witryn sieci Web, zawierające wyłącznie usługi WCF. Zabezpieczenia usług WCF jest zarządzana przy użyciu konfiguracji w *web.config* pliku. To sprawia, że uwierzytelnianie NTLM niepotrzebne.

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>Poziom dostępu do wygenerowanych klas ustawienie nie ma wpływu

Ustawienie **poziom do wygenerowanych klas dostępu** opcji **Konfigurowanie odwołania do usług** okno dialogowe **wewnętrzne** lub **Friend** może czasem nie działać. Nawet jeśli opcja jest wyświetlana w oknie dialogowym, wynikowa klasy obsługi są generowane z poziomem dostępu `Public`.

Jest to znane ograniczenie określonych typów, takich jak zserializowanym przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.

## <a name="error-debugging-service-code"></a>Błąd podczas debugowania kodu usługi

W przypadku wkroczyć do kodu dla usługi WCF z poziomu kodu klienta, może pojawić się błąd związany Brak symboli. Taka sytuacja może wystąpić, gdy usługi, które było częścią rozwiązania został przeniesiony lub usunięty z rozwiązania.

Po dodaniu odwołania do usługi WCF, która jest częścią bieżącego rozwiązania, między projektami usługi i projekt klienta usługi zostanie dodana zależność jawną kompilację. Gwarantuje to, czy klient zawsze ma dostęp do plików binarnych usługi aktualne, który jest szczególnie ważne w przypadku debugowania scenariuszy, takich jak przechodzenie z poziomu kodu klienta do kodu usługi.

Jeśli projekt usługi zostanie usunięty z rozwiązania, zostaje unieważniony tę zależność jawną kompilację. Programu Visual Studio może nie jest już zagwarantować, że zostanie ponownie skompilowany projekt usługi w razie.

Aby naprawić ten błąd, należy ręcznie ponownie skompilować projekt usługi:

1.  Na **narzędzia** menu, kliknij przycisk **opcje**.

2.  W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie wybierz pozycję **ogólne**.

3.  Upewnij się, że **Pokaż zaawansowane konfiguracje kompilacji** pole wyboru jest zaznaczone, a następnie kliknij przycisk **OK**.

4.  Załaduj projekt usługi WCF.

5.  W **programu Configuration Manager** okno dialogowe, zestaw **Konfiguracja rozwiązania aktywnego** do **debugowania**. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md).

6.  W **Eksploratora rozwiązań**, wybierz projekt usługi WCF.

7.  Na **kompilacji** menu, kliknij przycisk **odbudować** Aby ponownie skompilować projekt usługi WCF.

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>Usługi danych WCF nie są wyświetlane w przeglądarce

Podczas próby wyświetlenia Reprezentacja XML danych w [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], Internet Explorer mogą błędnie interpretuje dane jako źródła danych RSS. Upewnij się, że opcja wyświetlania źródeł danych RSS jest wyłączona.

Aby naprawić ten błąd, należy wyłączyć źródła danych RSS:

1.  W programie Internet Explorer na **narzędzia** menu, kliknij przycisk **Opcje internetowe**.

2.  Na **zawartości** na karcie **źródła** kliknij **ustawienia**.

3.  W **ustawienia źródła danych** okno dialogowe wyczyść **Włączanie źródła danych w widoku do czytania** pole wyboru, a następnie kliknij przycisk **OK**.

4.  Kliknij przycisk **OK** zamknąć **Opcje internetowe** okno dialogowe.

## <a name="see-also"></a>Zobacz także

- [Usługi Windows Communication Foundation i usługi danych WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)