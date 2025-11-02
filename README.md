from flask import Flask, request
import requests

app = Flask(__name__)

BOT_TOKEN = "7561021521:AAHIaNVU-Zr20ZWqBQV-kxWSgLP0rW3oXM"
CHAT_ID = "7561021521"

@app.route('/', methods=['POST'])
def webhook():
    data = request.get_json(force=True)
    message = data.get('message', '⚠️ Получен сигнал без текста')
    requests.post(f'https://api.telegram.org/bot{BOT_TOKEN}/sendMessage',
                  json={'chat_id': CHAT_ID, 'text': message})
    return 'ok', 200

if name == '__main__':
    app.run(host='0.0.0.0', port=5000)
