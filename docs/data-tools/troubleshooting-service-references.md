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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 28ff14f10cd6ad5612551bb65b7b17f0280358f3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72639601"
---
# <a name="troubleshoot-service-references"></a>Rozwiązywanie problemów z odwołaniami usługi

W tym temacie wymieniono typowe problemy, które mogą wystąpić podczas pracy z programem Windows Communication Foundation (WCF) lub Usługi danych programu WCF odwołaniami w programie Visual Studio.

## <a name="error-returning-data-from-a-service"></a>Błąd podczas zwracania danych z usługi

Po powrocie `DataSet` lub `DataTable` z usługi może zostać wyświetlony wyjątek "maksymalny przydział rozmiaru dla komunikatów przychodzących został przekroczony". Domyślnie właściwość `MaxReceivedMessageSize` niektórych powiązań jest ustawiona na stosunkowo niewielką wartość, aby ograniczyć narażenie na ataki typu "odmowa usługi". Można zwiększyć tę wartość, aby zapobiec wyjątku. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A>.

Aby naprawić ten błąd:

1. W **Eksplorator rozwiązań**kliknij dwukrotnie plik *App. config* , aby go otworzyć.

2. Znajdź Właściwość `MaxReceivedMessageSize` i zmień ją na większą.

## <a name="cannot-find-a-service-in-my-solution"></a>Nie można znaleźć usługi w rozwiązaniu

Po kliknięciu przycisku **odkryj** w oknie dialogowym **Dodawanie odwołań do usług** w ramach tego rozwiązania nie są wyświetlane co najmniej jeden projekt biblioteki usług WCF na liście usługi. Taka sytuacja może wystąpić, jeśli biblioteka usług została dodana do rozwiązania, ale nie została jeszcze skompilowana.

Aby naprawić ten błąd:

- W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt Biblioteka usługi WCF i kliknij polecenie **Kompiluj**.

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>Błąd podczas uzyskiwania dostępu do usługi za pośrednictwem pulpitu zdalnego

Gdy użytkownik uzyskuje dostęp do usługi WCF hostowanej w sieci Web za pośrednictwem połączenia pulpitu zdalnego, a użytkownik nie ma uprawnień administracyjnych, jest używane uwierzytelnianie NTLM. Jeśli użytkownik nie ma uprawnień administracyjnych, może zostać wyświetlony następujący komunikat o błędzie: "żądanie HTTP jest nieautoryzowane przez schemat uwierzytelniania klienta" anonimowe ". Nagłówek uwierzytelniania otrzymany z serwera to "NTLM". "

Aby naprawić ten błąd:

1. W projekcie witryny sieci Web otwórz stronę **Właściwości** .

2. Na karcie **Opcje uruchamiania** wyczyść pole wyboru **uwierzytelnianie NTLM** .

    > [!NOTE]
    > Uwierzytelnianie NTLM należy wyłączyć tylko dla witryn sieci Web, które zawierają wyłącznie usługi WCF. Zabezpieczenia usług WCF są zarządzane za pomocą konfiguracji w pliku *Web. config* . To sprawia, że uwierzytelnianie NTLM jest zbędne.

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>Ustawienie poziomu dostępu dla wygenerowanych klas nie ma żadnego wpływu

Ustawienie opcji **poziom dostępu dla wygenerowanych klas** w oknie dialogowym **Konfigurowanie odwołań** do usług **może** być niezawsze wykonywane. Mimo że opcja pojawia się w oknie dialogowym, powstałe klasy pomocy technicznej są generowane z poziomem dostępu `Public`.

Jest to znane ograniczenie niektórych typów, takie jak te serializowane przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.

## <a name="error-debugging-service-code"></a>Błąd podczas debugowania kodu usługi

Po przekroczeniu kodu dla usługi WCF z kodu klienta może zostać wyświetlony błąd związany z brakującymi symbolami. Taka sytuacja może wystąpić, gdy usługa, która była częścią rozwiązania, została przeniesiona lub usunięta z rozwiązania.

Podczas pierwszego dodawania odwołania do usługi WCF, która jest częścią bieżącego rozwiązania, do projektu usługi i projektu klienta usługi dodawana jest jawna zależność kompilacji. Gwarantuje to, że klient zawsze uzyskuje dostęp do aktualnych plików binarnych usługi, co jest szczególnie ważne w przypadku scenariuszy debugowania, takich jak Krokowe wykonywanie kodu klienta w kodzie usługi.

Jeśli projekt usługi zostanie usunięty z rozwiązania, ta jawna zależność kompilacji jest unieważniona. Program Visual Studio nie może już zagwarantować, że projekt usługi zostanie odbudowany w razie potrzeby.

Aby naprawić ten błąd, należy ręcznie skompilować ponownie projekt usługi:

1. W menu **Narzędzia** kliknij pozycję **Opcje**.

2. W oknie dialogowym **Opcje** rozwiń węzeł **projekty i rozwiązania**, a następnie wybierz pozycję **Ogólne**.

3. Upewnij się, że pole wyboru **Pokaż zaawansowane konfiguracje kompilacji** jest zaznaczone, a następnie kliknij przycisk **OK**.

4. Załaduj projekt usługi WCF.

5. W oknie dialogowym **Configuration Manager** Ustaw **aktywną konfigurację rozwiązania** na **debugowanie**. Aby uzyskać więcej informacji, zobacz [How to: Create and Edit Configurations](../ide/how-to-create-and-edit-configurations.md).

6. W **Eksplorator rozwiązań**wybierz projekt usługi WCF.

7. W menu **kompilacja** kliknij polecenie **Skompiluj ponownie** , aby ponownie skompilować projekt usługi WCF.

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>Usługi danych programu WCF nie są wyświetlane w przeglądarce

Gdy próbuje wyświetlić reprezentację XML danych w [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], program Internet Explorer może interpretować dane jako źródło danych RSS. Upewnij się, że opcja wyświetlania kanałów informacyjnych RSS jest wyłączona.

Aby naprawić ten błąd, wyłącz kanały informacyjne RSS:

1. W programie Internet Explorer w menu **Narzędzia** kliknij pozycję **Opcje internetowe**.

2. Na karcie **zawartość** w sekcji **źródła danych** kliknij pozycję **Ustawienia**.

3. W oknie dialogowym **Ustawienia kanału informacyjnego** wyczyść pole wyboru **Włącz widok do czytania źródła danych** , a następnie kliknij przycisk **OK**.

4. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Opcje internetowe** .

## <a name="see-also"></a>Zobacz także

- [Usługi Windows Communication Foundation i usługi danych WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)