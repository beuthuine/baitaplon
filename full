import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
import java.io.FileWriter;
import java.io.IOException;
import java.util.ArrayList;

public class TimKiemThongTin_NangCao extends JFrame implements ActionListener {

    private JTextArea txtKetQua, txtLichSu;
    private JTextField txtKey1, txtKey2, txtKey3;
    private JButton btnTimKiem, btnTimGia, btnXuatFile, btnXoa;
    private JComboBox<String> cboWebsite;
    private int soLanTim = 0;

    private ArrayList<String> lichSu = new ArrayList<>();

    public TimKiemThongTin_NangCao() {
        setTitle("HỆ THỐNG TÌM KIẾM THÔNG TIN & GIÁ SẢN PHẨM");
        setSize(1000, 600);
        setLocationRelativeTo(null);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        JPanel panel = new JPanel();
        panel.setLayout(null);
        add(panel);

        // Danh sách web
        JLabel lblWeb = new JLabel("Chọn Website:");
        lblWeb.setBounds(30, 30, 150, 25);
        panel.add(lblWeb);

        String[] websites = {"Google", "Dantri", "VnExpress", "Shopee", "Tiki"};
        cboWebsite = new JComboBox<>(websites);
        cboWebsite.setBounds(170, 30, 200, 25);
        panel.add(cboWebsite);

        // Từ khóa
        JLabel lbl1 = new JLabel("Từ khóa 1:");
        lbl1.setBounds(30, 80, 100, 25);
        panel.add(lbl1);

        txtKey1 = new JTextField();
        txtKey1.setBounds(130, 80, 240, 25);
        panel.add(txtKey1);

        JLabel lbl2 = new JLabel("Từ khóa 2:");
        lbl2.setBounds(30, 120, 100, 25);
        panel.add(lbl2);

        txtKey2 = new JTextField();
        txtKey2.setBounds(130, 120, 240, 25);
        panel.add(txtKey2);

        JLabel lbl3 = new JLabel("Từ khóa 3:");
        lbl3.setBounds(30, 160, 100, 25);
        panel.add(lbl3);

        txtKey3 = new JTextField();
        txtKey3.setBounds(130, 160, 240, 25);
        panel.add(txtKey3);

        // Nút chức năng
        btnTimKiem = new JButton("Tìm kiếm tin");
        btnTimKiem.setBounds(60, 220, 140, 40);
        btnTimKiem.addActionListener(this);
        panel.add(btnTimKiem);

        btnTimGia = new JButton("Tìm giá SP");
        btnTimGia.setBounds(220, 220, 140, 40);
        btnTimGia.addActionListener(this);
        panel.add(btnTimGia);

        btnXuatFile = new JButton("Xuất file");
        btnXuatFile.setBounds(60, 280, 140, 40);
        btnXuatFile.addActionListener(this);
        panel.add(btnXuatFile);

        btnXoa = new JButton("Xóa dữ liệu");
        btnXoa.setBounds(220, 280, 140, 40);
        btnXoa.addActionListener(this);
        panel.add(btnXoa);

        // Kết quả
        JLabel lblKQ = new JLabel("KẾT QUẢ");
        lblKQ.setBounds(470, 10, 200, 30);
        panel.add(lblKQ);

        txtKetQua = new JTextArea();
        JScrollPane scroll1 = new JScrollPane(txtKetQua);
        scroll1.setBounds(420, 40, 260, 460);
        panel.add(scroll1);

        // Lịch sử
        JLabel lblLS = new JLabel("LỊCH SỬ TÌM KIẾM");
        lblLS.setBounds(760, 10, 200, 30);
        panel.add(lblLS);

        txtLichSu = new JTextArea();
        JScrollPane scroll2 = new JScrollPane(txtLichSu);
        scroll2.setBounds(710, 40, 260, 460);
        panel.add(scroll2);
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        String web = cboWebsite.getSelectedItem().toString();
        String key1 = txtKey1.getText();
        String key2 = txtKey2.getText();
        String key3 = txtKey3.getText();

        if (e.getSource() == btnTimKiem) {
            soLanTim++;
            txtKetQua.setText("Kết quả tìm tin trên: " + web + "\n\n");

            if (!key1.isEmpty()) txtKetQua.append(" - Có 4 bài viết về: " + key1 + "\n");
            if (!key2.isEmpty()) txtKetQua.append(" - Có 2 bài viết về: " + key2 + "\n");
            if (!key3.isEmpty()) txtKetQua.append(" - Có 5 bài viết về: " + key3 + "\n");

            txtKetQua.append("\nSố lần tìm: " + soLanTim);

            luuLichSu(web, key1, key2, key3, "Tin tức");
        }

        if (e.getSource() == btnTimGia) {
            soLanTim++;
            txtKetQua.setText("Kết quả tìm giá sản phẩm trên: " + web + "\n\n");

            if (!key1.isEmpty()) txtKetQua.append(" - " + key1 + " : 3.200.000 VNĐ\n");
            if (!key2.isEmpty()) txtKetQua.append(" - " + key2 + " : 5.800.000 VNĐ\n");
            if (!key3.isEmpty()) txtKetQua.append(" - " + key3 + " : 1.950.000 VNĐ\n");

            txtKetQua.append("\nSố lần tìm: " + soLanTim);

            luuLichSu(web, key1, key2, key3, "Giá SP");
        }

        if (e.getSource() == btnXoa) {
            txtKetQua.setText("");
            txtLichSu.setText("");
            txtKey1.setText("");
            txtKey2.setText("");
            txtKey3.setText("");
            soLanTim = 0;
        }

        if (e.getSource() == btnXuatFile) {
            try {
                FileWriter writer = new FileWriter("ketqua.txt");
                writer.write(txtKetQua.getText());
                writer.close();
                JOptionPane.showMessageDialog(this, "Xuất file thành công!");
            } catch (IOException ex) {
                JOptionPane.showMessageDialog(this, "Lỗi khi xuất file!");
            }
        }
    }

    private void luuLichSu(String web, String key1, String key2, String key3, String loai) {
        String text = "[" + loai + "] " + web + " => "
                + key1 + " | " + key2 + " | " + key3;
        lichSu.add(text);

        txtLichSu.setText("");
        for (String s : lichSu) {
            txtLichSu.append(s + "\n");
        }
    }

    public static void main(String[] args) {
        new TimKiemThongTin_NangCao().setVisible(true);
    }
}
