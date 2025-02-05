import smtplib
from email.mime.text import MIMEText
from email.mime.multipart import MIMEMultipart

def enviar_email_teste(remetente, senha_aplicativo, destinatario, servidor_smtp, porta):
    try:
        # faz conexão com o servidor SMTP
        with smtplib.SMTP(servidor_smtp, porta) as servidor:
            # Usa um servidor TLS para enviar o e-mail
            servidor.starttls()
            # Login no servidor
            servidor.login(remetente, senha_aplicativo)
            
            # Assunto e mensagem (formatação corrigida)
            assunto = "teste do assunto"
            mensagem = "Email de teste automação da inteligência artificial. Com acentos e ç."
            
            # Usei o MIMEText para mudar a formatação (UTF-8)
            msg = MIMEMultipart()
            msg['From'] = remetente
            msg['To'] = destinatario
            msg['Subject'] = assunto
            
            # Corpo da mensagem
            corpo_email = MIMEText(mensagem, 'plain', 'utf-8')
            msg.attach(corpo_email)

            # Envia o e-mail
            servidor.sendmail(remetente, destinatario, msg.as_string())
            print("E-mail de teste enviado com sucesso!")
    
    except Exception as e:
        print(f"Erro ao enviar e-mail: {e}")

# Credenciais que vamos usar para enviar os e-mails
remetente = "gooldmaster38@gmail.com"
senha_aplicativo = "xutv qgkn nuwt uyzl"  # Senha de aplicativo
destinatario = "mau691479@gmail.com"
servidor_smtp = "smtp.gmail.com"
porta = 587

enviar_email_teste(remetente, senha_aplicativo, destinatario, servidor_smtp, porta)
