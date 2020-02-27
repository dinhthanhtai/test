package quanlynhansu;

import java.util.Scanner;

public class NhanVien {
	protected String NgaySinh;
	protected String HoTen;
	public int Luong;

	Scanner scanner = new Scanner(System.in);

	public void nhap() {
		System.out.println("Nhap ho ten: ");
		HoTen = scanner.nextLine();
		System.out.println("Nhap ngay sinh: ");
		NgaySinh = scanner.nextLine();
		System.out.println("Nhap he so luong: ");
		Luong = scanner.nextInt();
	}

	public String getNgaySinh() {
		return NgaySinh;
	}

	public void setNgaySinh(String ngaySinh) {
		NgaySinh = ngaySinh;
	}

	public String getHoTen() {
		return HoTen;
	}

	public void setHoTen(String hoTen) {
		HoTen = hoTen;
	}

	public int getLuong() {
		return Luong;
	}

	public void setLuong(int luong) {
		Luong = luong;
	}

	public String xuat() {
		return "Ho ten: " + this.HoTen + ", Ngay Sinh: " + this.NgaySinh + ", He So Luong: " + this.Luong;
	}
}


package quanlynhansu;

public class GiamDoc extends NhanVien {
	public GiamDoc() {
        super();
    }
}

package quanlynhansu;

import java.util.Scanner;

public class QuanDoc extends NhanVien {
	 private int soNV;

	    public QuanDoc() {
	        super();
	    }

	    public QuanDoc(int soNV) {
	        super();
	        this.soNV = soNV;
	    }

	    public int getSoNV() {
	        return soNV;
	    }

	    public void setSoNV(int soNV) {
	        this.soNV = soNV;
	    }
	    @Override
	    public void nhap(){
	        super.nhap();
	        System.out.println("Nhap so luong nhan vien quan ly: ");
	        soNV=scanner.nextInt();
	    }
	    @Override
	    public String xuat() {
			return "Ho ten: " + this.HoTen + ", Ngay Sinh: " + this.NgaySinh + ", He So Luong: " + this.Luong + ", So luong nhan vien quan ly: "+ this.soNV;
	    	
	    }
	   
	    
}


package quanlynhansu;

import java.util.Scanner;

import com.sun.org.apache.bcel.internal.generic.SWAP;

public class Main {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Scanner scanner = new Scanner(System.in);
		int snv, choice;
		NhanVien[] nv = new NhanVien[50];
		while(true) {
			System.out.println("===========Menu=========");
			System.out.println("1. nhap thong tin nhan vien");
			System.out.println("2. xuat thong tin nhan vien");
			System.out.println("3. xuat nhan vien co luong cao nhat");
			System.out.println("4. xuat  nguoi co ho la nguyen");
			System.out.println("5. sap xep nhan vien tang dan theo luong");
			System.out.println("6. thoat");
			System.out.println("vui long nhap lua chon.");
			choice = scanner.nextInt();
			switch (choice) {
			case 1: {
				System.out.println("nhap so nhan vien: ");
				snv = scanner.nextInt();
				nv = new NhanVien[snv];
				for (int i = 0; i < snv; i++) {
					System.out.println("1. Nhap ifo giam doc.");
					System.out.println("2. Nhap ifo quan doc.");
					System.out.println("3. Nhap ifo nhan vien.");
					int t = scanner.nextInt();
					switch (t) {
					case 1:
						nv[i] = new GiamDoc();
						break;
					case 2:
						nv[i] = new QuanDoc();
						break;
					case 3:
						nv[i] = new NhanVien();
						break;
					}
					nv[i].nhap();
					break;
				}
				break;
			}
			case 2: {
				for (NhanVien nv1 : nv) {
					System.out.println(nv1.xuat());
				}
				;
				break;
			}
			case 3:
				int max = 0;
				for (int i = 0; i < nv.length; i++) {
					if (nv[i].getLuong() > max) {
						max = nv[i].getLuong();
					}
					;
					System.out.println("nguoi co luong cao nhat: " + max * 100000);
					break;

				}
			case 4: {
				System.out.println("nguoi co ho la 'nguyen': ");
				for (int i = 0; i < nv.length; i++) {
					if (nv[i].getHoTen().equals("nguyen")) {
						System.out.println(nv[i].getHoTen());
					}
				}
			}
			case 5: {
				int temp;
				System.out.println("thu tu tang dan theo luong: ");
				for (int i = 0; i < nv.length; i++) {
					for (int j = i + 1; j < nv.length; j++) {
						if (nv[i].getLuong() > nv[j].getLuong()) {
							SWAP(nv[i], nv[j]);
						}
					}
				}
			}
			case 6:
				return;
			}

		}
	}

	private static void SWAP(NhanVien nhanVien, NhanVien nhanVien2) {
		NhanVien Temp;
		Temp = nhanVien;
		nhanVien = nhanVien2;
		nhanVien2 = Temp;

	}

}
