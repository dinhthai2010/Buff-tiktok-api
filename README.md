from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route('/buff/view', methods=['POST'])
def buff_view():
    data = request.get_json()
    video_url = data.get('url')
    amount = data.get('amount')

    if not video_url or not amount:
        return jsonify({'status': 'error', 'message': 'Thiếu thông tin'}), 400

    return jsonify({
        'status': 'success',
        'message': f'Đã gửi yêu cầu buff {amount} view đến video: {video_url}',
        'fake_process_id': 'buff12345xyz'
    })

if __name__ == '__main__':
    app.run()
