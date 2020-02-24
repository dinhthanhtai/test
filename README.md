package quanlynhansu;

import java.util.Scanner;

public class NhanVien {
	protected String NgaySinh;
	String HoTen;
	int Luong;

	Scanner scanner = new Scanner(System.in);

	public void nhap() {
		System.out.println("Nhap ho ten: ");
		String HoTen = scanner.nextLine();
		System.out.println("Nhap ngay sinh: ");
		String NgaySinh = scanner.nextLine();
		System.out.println("Nhap he so luong: ");
		int l = scanner.nextInt();
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
	
}


package quanlynhansu;

import java.util.Scanner;

public class QuanDoc extends NhanVien {
}


package quanlynhansu;

import java.util.Scanner;

import com.sun.org.apache.bcel.internal.generic.SWAP;

public class Main {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		
		Scanner scanner = new Scanner(System.in);
		System.out.println("nhap so nhan vien: ");
		int snv = scanner.nextInt();
		NhanVien[] nv = new NhanVien[snv];
		for(int i = 0; i < snv; i++) {
			System.out.println("1. Nhap ifo giam doc.");
			System.out.println("2. Nhap ifo quan doc.");
			System.out.println("3. Nhap ifo nhan vien.");
			int t = scanner.nextInt();
			switch(t) {
			case 1: nv[i] = new GiamDoc(); break;
			case 2: nv[i] = new QuanDoc(); break;
			case 3: nv[i] = new NhanVien(); break;
			}
			nv[i].nhap();
		}
		for(int i = 0 ; i < snv; i++) {
			System.out.println(nv[i].xuat());
		}
		//3.
		int max = 0 ;
		for ( int i = 0 ; i < snv; i++) {
			if(nv[i].getLuong() > max) {
				max = nv[i].getLuong();
			}
		}
		System.out.println("nguoi co luong cao nhat: " + max);
		//4.
		System.out.println("nguoi co ho la 'nguyen': ");
		for(int i = 0; i < snv ; i++) {
			if(nv[i].getHoTen().equals("nguyen")) {
				System.out.println(nv[i].getHoTen());
			}
		}
		//5.
		int temp = 0;
		System.out.println("thu tu tang dan theo luong: ");
		for(int  i = 0; i< snv; i++) {
			for (int j = i+1; j < snv; j++) {
				if(nv[i].getLuong() > nv[j].getLuong()) {
					nv[temp] = nv[i];
					nv[i] = nv[j];
					nv[j] = nv[temp];
				}
			}
		}
	}

}
